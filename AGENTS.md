# Repository working notes

These notes are for automated coding assistants and contributors working in this fork.

## Pull request discipline

- Keep each pull request narrowly scoped to one feature, bug fix, or refactor. Do not bundle unrelated cleanup.
- Start from the intended upstream base and verify the exact base SHA before preparing the PR.
- Keep the diff minimal. If validation-only files or temporary CI workflows are needed, use a separate branch and do not include them in the final PR unless they are part of the feature.
- Write the PR description as normal engineering communication for a maintainer: concise, factual, specific, and easy to review.
- Do not include prompt transcripts, assistant/tool chatter, generated-analysis commentary, AI attribution, or other meta text in public PR titles, commit messages, descriptions, comments, or code.
- Avoid generic filler, exaggerated claims, sales language, excessive headings, and repetitive restatement of the diff.
- Explain why the change exists, what behavior changes, what remains unchanged, and any important compatibility constraint.
- When a PR follows maintainer feedback, acknowledge that feedback directly and neutrally, then show how the revised change addresses it. Do not argue with or editorialize about the previous review.
- Report validation precisely. Distinguish compile/check success, CI success, artifact generation, physical device testing, and final runtime validation. Never claim a test or hardware result that was not actually observed.
- Mention limitations or incomplete validation when they matter to review.
- Prefer exact commands, targets, platforms, and measured results over vague statements such as "fully tested".
- Before opening the PR, inspect the final commit list and diff against the upstream base. Confirm that only intended files and commits are present.
- Do not add co-author trailers, generated-by markers, or tooling attribution unless explicitly requested by the repository maintainer or contributor.

## Commit style

- Use short conventional commit-style subjects when they match the repository history, for example `fix(...)`, `feat(...)`, `perf(...)`, `build(...)`, or `docs(...)`.
- Keep commits focused and reviewable. Validation-only experiments should not leak into the final feature commit history.
- Do not rewrite or force-push shared work without explicit approval.

## Review checklist before publishing

Confirm all of the following:

1. The base branch and base SHA are correct.
2. The branch contains only the intended commits.
3. The diff contains only the intended files and behavior.
4. Formatting/tests/CI relevant to the change have been run and their results are known.
5. Hardware validation is described only if it actually happened.
6. The PR text contains no local paths, secrets, temporary worktree names, prompt/tool output, or unrelated project context.
7. The PR reads like a normal maintainer-facing engineering contribution, not a transcript of how it was produced.

## Mandatory factual release changelog

This rule applies to every GitHub Release, build release, prerelease, and future automated publishing workflow in this repository. Both Codex and Claude must follow it.

1. Every release must describe **real, specific changes since the previous release**, based on actual commits and the code diff. Explain what changed and where; include issue/commit references and any known limitations. Do not claim untested fixes or unsupported capabilities.
2. Never use generic filler such as "bug fixes", "performance improvements", "misc updates", "new features", or a copied/static note as the entire changelog. If a release only rebuilds the same source, label it as a **rebuild only** and state exactly what packaging, toolchain, signing, or artifact metadata changed. Do not invent application changes.
3. Keep the GitHub Release description and root `CHANGELOG.md` aligned. The `Factual release changelog` workflow audits actual source commits, adds evidence-linked notes to the release, and records the release in `CHANGELOG.md`. A failed audit is a release-policy failure that must be corrected, not ignored or disabled.
4. Release-producing workflows must prepare truthful release notes before publication. Treat the post-publication audit as an additional check, not permission to publish placeholders; never bypass the check or mark it non-blocking.
5. When a release contains user-facing assets, ensure version numbers and repo feeds also match the release. Existing installed-version rules remain in effect.

These instructions apply to changes by humans, GitHub Actions, Claude, Codex, and any other automation.
