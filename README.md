<div align="center">

# GitHub Mastery Guide

### A complete technical reference — from Git internals to enterprise DevOps

[![Git](https://img.shields.io/badge/Git-2.39+-F05032?logo=git&logoColor=white&style=flat-square)](https://git-scm.com)
[![GitHub](https://img.shields.io/badge/Platform-GitHub-181717?logo=github&logoColor=white&style=flat-square)](https://github.com)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-2088FF?logo=githubactions&logoColor=white&style=flat-square)](https://github.com/features/actions)
[![License](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey?style=flat-square)](https://creativecommons.org/licenses/by/4.0/)

*Five modules · Internals to platform engineering · Diagrams · Real-world patterns*

</div>

---

## Table of Contents

| # | Module | Core Topics | Depth |
|:-:|--------|-------------|:-----:|
| 01 | [**Fundamentals**](./01-fundamentals.md) | Git object model · refs · branching · merging · rebasing | `●●●○○` |
| 02 | [**Collaboration**](./02-collaboration.md) | Issues · Pull Requests · Code Review · Projects · CODEOWNERS | `●●●○○` |
| 03 | [**GitHub Actions**](./03-actions.md) | Workflows · triggers · matrix · secrets · reusable workflows · custom actions | `●●●●○` |
| 04 | [**Advanced Platform**](./04-advanced.md) | CLI · REST API · GraphQL · webhooks · security · packages | `●●●●●` |
| 05 | [**Git Workflows**](./05-git-workflows.md) | GitHub Flow · GitFlow · trunk-based · release strategies | `●●●●○` |

---

## Who This Guide Is For

> **Target audience:** Engineers who know the basics and want to work at the edge of the platform.

You should already know:

- [x] `git add`, `git commit`, `git push`
- [x] What a branch is
- [x] What a pull request is

This guide builds from there — covering the *why* behind Git's design, the full surface of GitHub's collaboration and automation platform, and the patterns used by high-performing engineering teams.

---

## Quick-Start Reference

### Repository Bootstrap

```bash
# Standard clone
git clone https://github.com/owner/repo.git

# Shallow clone — fastest for large repos (CI, build agents)
git clone --depth 1 https://github.com/owner/repo.git

# Restore full history later
git fetch --unshallow

# Clone a specific branch
git clone --branch release/2.0 --single-branch https://github.com/owner/repo.git
```

### Daily Driver Commands

| Action | Command | Key Detail |
|--------|---------|------------|
| Create + switch branch | `git switch -c feat/name` | Modern `checkout -b` |
| Stage in hunks | `git add -p` | Interactive — never over-commit |
| Commit with message | `git commit -m "feat(auth): add OAuth2 flow"` | Conventional Commits format |
| Amend last commit | `git commit --amend --no-edit` | Unpushed commits only |
| Soft undo last commit | `git reset HEAD~1` | Keeps working tree changes |
| Named stash | `git stash push -m "wip: auth refactor"` | Findable later |
| List stashes | `git stash list` | `stash@{0}` is newest |
| Commits ahead of main | `git log main..HEAD --oneline` | Before opening a PR |
| Interactive rebase | `git rebase -i HEAD~5` | Squash, reword, drop |
| Show file at commit | `git show abc1234:src/app.ts` | Without checkout |

### GitHub CLI One-Liners

```bash
# Pull Requests
gh pr create --fill --assignee @me --draft
gh pr view --web                          # Open in browser
gh pr merge --squash --delete-branch

# Issues
gh issue create --title "Bug: login fails" --label bug
gh issue list --label "priority:high" --state open --json number,title

# Actions
gh run list --workflow=ci.yml
gh run watch                              # Tail live output
gh run rerun --failed                     # Retry only failed jobs

# Repos
gh repo create myorg/myrepo --private --clone
gh repo fork owner/repo --clone --remote

# API (raw access)
gh api repos/{owner}/{repo}/actions/runs --jq '.workflow_runs[0].status'
```

---

## How to Navigate This Guide

```
README  ←  You are here
  │
  ├── 01-fundamentals.md ──── "How does Git actually work?"
  │     └── Object model, SHA hashing, refs, merge strategies
  │
  ├── 02-collaboration.md ─── "How do teams work effectively?"
  │     └── Issues, PRs, review, projects, branch protection
  │
  ├── 03-actions.md ──────── "How do I automate everything?"
  │     └── CI/CD, matrix builds, custom actions, secrets
  │
  ├── 04-advanced.md ─────── "How do I build on the platform?"
  │     └── API, CLI, webhooks, security, packages, pages
  │
  └── 05-git-workflows.md ── "What branching strategy should we use?"
        └── GitFlow, trunk-based, release management
```

Each module is **self-contained** — jump to any section directly. Cross-module references are marked with 🔗.

---

## Tools Referenced

| Tool | Install | Purpose |
|------|---------|---------|
| `git` ≥ 2.39 | [git-scm.com](https://git-scm.com) | Version control core |
| `gh` CLI | `brew install gh` · `winget install GitHub.cli` | GitHub from terminal |
| VS Code + GitHub extension | Via VS Code marketplace | In-editor code review |
| GitHub Desktop | [desktop.github.com](https://desktop.github.com) | GUI option |
| `jq` | `brew install jq` | JSON processing for API work |

---

## Conventions Used in This Guide

| Callout | Meaning |
|---------|---------|
| `> **Note**` | General information worth knowing |
| `> **Tip**` | A practical shortcut or best practice |
| `> **Warning**` | Action could cause data loss or problems |
| `> **Danger**` | Destructive — requires explicit understanding |

---

<div align="center">

*Content verified against GitHub documentation as of 2025. Open an issue for corrections.*

</div>
