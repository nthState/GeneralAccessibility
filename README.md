# GeneralIdentifiers

Dynamically generate nested structs for use in accessibility identifiers/analytic keys

Given a source file (GeneralIdentifiers.csv)

```
Home,playButton,Play
Home,pauseButton,Pause
```

It will generate a nested struct that you can reference like:

```
let data = GeneralIdentifiers.playButton.play()
```

## Support

- Current version supports list to nested struct generation

## What's next

- JSON decoder
- Think about how we can move the `GeneralIdentifiers(.json/.csv)` so that they can be customizable by the user, as you can only set a path relative to the package.

## Configuration

Update the `SourceGeneratorConfiguration.json` to specify output preferences:

```
{
  "outputCasing": "camelCase",
  "sourceName": "GeneralIdentifiers.csv"
}
```

## How does it work

It uses `BuildToolPlugin` to run as a pre-build step which:

- Scans the source file
- Generates an extension to `GeneralIdentifiers`
- Passes this file to the `build` step of the Swift Package

The outcome is a nested struct type.

For more inforamation about `BuildToolPlugin` take a look here:  https://github.com/apple/swift-evolution/blob/main/proposals/0303-swiftpm-extensible-build-tools.md
