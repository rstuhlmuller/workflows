# workflows

GitHub workflows for the organization

[![Super-Linter](https://github.com/Stuhlmuller/workflows/actions/workflows/lint.yml/badge.svg)](https://github.com/marketplace/actions/super-linter)

## Reusable workflows

This repository publishes reusable GitHub Actions workflows for repositories in the Stuhlmuller organization.

- `.github/workflows/release.yml` runs semantic-release, with an optional dry-run mode for pull requests.
- `.github/workflows/terragrunt-plan.yml` runs the homelab Terragrunt plan path.
- `.github/workflows/terragrunt-apply.yml` runs the homelab Terragrunt apply path.
- `.github/workflows/validate.yml` runs the homelab validation checks.

Call them from another repository with a job-level `uses` reference:

```yaml
jobs:
  validate:
    uses: Stuhlmuller/workflows/.github/workflows/validate.yml@main

  terragrunt-plan:
    uses: Stuhlmuller/workflows/.github/workflows/terragrunt-plan.yml@main
    permissions:
      contents: read
      id-token: write
      pull-requests: write
    secrets: inherit

  terragrunt-apply:
    uses: Stuhlmuller/workflows/.github/workflows/terragrunt-apply.yml@main
    permissions:
      contents: read
      id-token: write
    secrets: inherit
```
