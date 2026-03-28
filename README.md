# Reusable GitHub Workflows

This repository contains public, reusable workflows for GitHub.

## Validate GitHub workflows files

Validate all of the GitHub workflows files in the standard `.github/workflows`
directory are valid YAML and have the correct filename extension.

### Inputs

#### `uses_reviewdog_actionlint`

Determine if reviewdog/action-actionlint@v1 should be used. Optional, defaults
to `true`.

#### `validate_file_extensions`

Check that the workflow file has the correct YAML filename extension (see also
        `yaml_filename_extension`). Optional, defaults to `true`.

#### `yaml_filename_extension`

The required YAML filename extension (no leading dot). Optional, defaults to
`yaml`.

## Example workflow

To call this workflow place create a file called
`.github/workflows/validate-workflows.yaml` in your repository. The file
contents should looks similar to this:

~~~ yaml
name: Validate workflows

on:
  pull_request:
    paths:
      - '.github/workflows/**'
  workflow_dispatch:

permissions:
  contents: read

jobs:
  build:
    uses: stevemarple/workflows/.github/workflows/validate-workflows.yaml@stable
~~~
