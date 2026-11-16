# Maintaining this REA fork

This repository is the user's fork of the official
[morluto/rea](https://github.com/morluto/rea) project.

## Daily upstream sync

The workflow `.github/workflows/upstream-sync.yml` checks the official
upstream `main` branch every day at 09:40 UTC. It uses GitHub's **Sync a fork
branch with the upstream repository** API to update this fork's `main` when
upstream has new commits.

- The workflow verifies that this repository is still a fork of
  `morluto/rea`.
- It compares the fork's `main` with `morluto:main` before writing.
- It performs no write when the fork is already current.
- It uses GitHub's upstream-sync operation; it does not force-push.
- If GitHub reports a merge conflict, permission problem, or other error, the
  workflow fails visibly and does not overwrite either side.
- The run summary records the upstream release and published
  `rea-agents` npm version for context.

## What it does not update

A GitHub fork sync updates repository source. It does **not** update a local
npm CLI, Codex Marketplace plugin, MCP registration, Node.js runtime, or
optional analysis provider on a personal computer.

Update the local installation according to how REA was installed:

- Global npm/bun CLI: use the official `rea update` flow.
- Codex Marketplace plugin: use the supported Codex plugin/marketplace
  update flow.
- Setup-owned MCP registration: review the official setup plan, apply only
  the intended client changes, then restart/reconnect and verify the live
  tool catalog.

Official sources:

- https://github.com/morluto/rea
- https://rea.tools
- https://github.com/morluto/rea/releases

## First-run note

GitHub Actions must be enabled for this fork. After the workflow is merged,
check the Actions tab once. If GitHub displays an enable-workflows prompt for
the fork, enable it. The scheduled job will then run daily; it can also be
started manually from the workflow page.
