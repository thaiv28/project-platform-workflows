# Project Platform Workflows

Public, credential-free reusable GitHub Actions workflows for projects published through `thaiv.dev`.

Application repositories own their builds and call these workflows. AWS access uses GitHub OIDC and a repository secret containing only the deployment role ARN; no long-lived AWS credentials belong here.

## Contracts

- `schemas/project-manifest.schema.json` defines version 1 of the project manifest.
- `.github/workflows/deploy-static.yml` publishes immutable static releases, promotes the selected revision, invalidates CloudFront, and checks deployment health.
- Successful releases remain under `releases/<git-sha>` so infrastructure automation can retain the five newest artifacts.

Infrastructure provisioning and project registration remain in the private infrastructure repository.
