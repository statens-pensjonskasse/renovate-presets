# Renovate Configuration files for Statens Pensjonskasse's projects

See https://docs.renovatebot.com/config-presets/

To use our Renovate presets in your project: 
1. Choose the preset that fits your project from this repository
2. Add a `.github/renovate.json` similar to this:

```json
{
  "extends": [
    "github>statens-pensjonskasse/renovate-presets:daily-automerge-non-major"
  ]
}
```

This example imports the configuration for daily automerge of updates that are not major.

## Spring-Boot Java APIs
For Spring-Boot java APIs we recommend only renovating patch versions of spring-boot by including the `spring-boot-patch-updates-only` preset:
(Then manually updating major and minor versions when all applications are ready)

```json
{
  "extends": [
    "github>statens-pensjonskasse/renovate-presets:daily-automerge-non-major",
    "github>statens-pensjonskasse/renovate-presets:spring-boot-patch-updates-only.json"
  ]
}
```

## Renovate Comments
For other types of dependencies like github releases or helm charts you can use the `renovate-comments` preset by specifying the file extensions you want to scan for dependencies as follows

```json
{
  "extends": [
    "github>statens-pensjonskasse/renovate-presets:daily-automerge-non-major",
    "github>statens-pensjonskasse/renovate-presets:renovate-comments(\\.yaml$,(\\.yml$))"
  ]
}
```

This will scan for renovate comments about dependencies in files with the extensions `.yaml` and `.yml` on this format
```yaml
      with:
        gh-cli-version: 2.65.0 # renovate: github-releases=cli/cli
```
This tells Renovate to look for github-release from the repository `cli/cli` and the current version is `2.65.0`