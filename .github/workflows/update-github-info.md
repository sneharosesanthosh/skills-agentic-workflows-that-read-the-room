---
name: update-github-info
description: Review recent official GitHub updates and propose practical content updates for Mona's website.
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
strict: true
network:
  allowed:
    - github.blog
    - github.com
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Read `notes/mona-notes.md` before making any changes. Fetch the latest official
GitHub updates from:

- https://github.blog/latest/
- https://github.blog/changelog/

Use those sources to update `site/content/github-info.md` with short, practical
guidance for developers. Mention the source whenever an update comes from the
GitHub Blog or GitHub Changelog, and preserve the existing editorial angle and
Markdown structure.

When an update is needed, use the configured `create-pull-request` safe output
to propose the change for Mona to review. Do not write directly to `main`, and
do not modify any file other than `site/content/github-info.md`. If no useful
official update is available, make no file changes and call `noop` with a brief
explanation.