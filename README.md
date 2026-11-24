# coderabbit

Org-wide [CodeRabbit](https://coderabbit.ai) review settings for every
`shotledger` repository.

CodeRabbit reads [`.coderabbit.yaml`](.coderabbit.yaml) from the default
branch of this repository and applies it to any repository in the org that
has no `.coderabbit.yaml` of its own
([central configuration](https://docs.coderabbit.ai/configuration/central-configuration)).
The repository name must stay `coderabbit`.

## Defaults

- `chill` review profile.
- Summary in the walkthrough comment; the PR body is left alone.
- Renovate and Dependabot PRs are not reviewed.
- Draft PRs are not reviewed. Comment `@coderabbitai review` to ask for one.
- Lockfiles are skipped.

## Repository rules

A repository that needs its own rules adds a small `.coderabbit.yaml` with
`inheritance: true` and only its own path filters and path instructions.
Without `inheritance: true` that file replaces these defaults entirely.

Note that a repository with no file of its own takes its code guidelines
(`AGENTS.md`, `CLAUDE.md`) from this repository, not its own. A repository
whose `AGENTS.md` matters for reviews needs its own file.

To check what applies, comment `@coderabbitai configuration` on a PR.

## Notes

- A CodeRabbit approval does not count toward required reviews.
- Where the branch rules require conversation resolution, each CodeRabbit
  comment blocks the merge until it is resolved.
