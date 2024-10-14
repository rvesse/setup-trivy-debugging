# Setup Trivy Action Debugging

A small repository to provide example GitHub workflows that demonstrate issues with using the
https://github.com/aquasecurity/setup-trivy action.

Essentially since they introduced the setup action it no longer avoids repeated work, so if you call
https://github.com/aquasecurity/trivy-action more than once in your workflow you get Trivy installed multiple times
which is wasted effort and could lead to hitting rate limiting errors.

There are several example workflows in this repository:

- [`setup-trivy-indirect.yml`](.github/workflows/setup-trivy-indirect.yml) which only calls the main `trivy-action`
  but demonstrates that `setup-trivy` is getting called multiple times as a result
- [`setup-trivy-only-latest.yml`](.github/workflows/setup-trivy-only.yml) which calls `setup-trivy` directly and demonstrates
  that if called multiple times `trivy` is installed multiple times.
    - There are also variants with `-v0.1.0` and `-v0.2.0` suffixes that test those specific versions of the
      `setup-trivy` action