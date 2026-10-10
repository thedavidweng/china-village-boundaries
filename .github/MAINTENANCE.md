# Static repository maintenance

Repository data and application files are edited manually. No generation job runs.
Routine workflow lint and orphaned Dependabot auto-merge have been retired after
one-time jactionlint 2.0.2 default validation. No scheduled jobs or updater feeds
are required for this frozen repository.

The Codeberg mirror runs on branch/tag push or workflow_dispatch. Mirror writes
are serialized and never cancel an in-progress sync. GitHub token permission is
contents:read and checkout credentials are not persisted. CODEBERG_TOKEN needs
write permission for the target repository on Codeberg. The action force-syncs
remote branches and tags; it uses its own Codeberg credentials.

Manual sync: `gh workflow run mirror.yml --repo thedavidweng/china-village-boundaries --ref main`.
Inspect the result with `gh run list --repo thedavidweng/china-village-boundaries --workflow mirror.yml`.
For local validation run jactionlint 2.0.2 with `--version`,
`--profile default --format summary`, and `--diff`; review suggested edits.
