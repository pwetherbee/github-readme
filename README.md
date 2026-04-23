# GitHub Contribution Art

This repo generates the SVGs for your GitHub profile README.

Your actual profile README should live in a separate repository named exactly:

- `colincode0/colincode0`

## Local preview

```bash
python generate_contribs.py --mock --out output
```

## GitHub setup

1. In this repo, go to `Settings -> Secrets and variables -> Actions`.
2. Add a repository secret named `GH_README_TOKEN`.
3. Use a GitHub personal access token for that secret.
4. If you want private contributions included, use a token with `read:user` and `repo`.
5. In `Actions`, enable workflows for the repo if they are not already enabled.
6. Run the `Update Contribution Art` workflow once with `Run workflow`.

If `GH_README_TOKEN` is missing, the workflow falls back to the built-in `GITHUB_TOKEN`, which is usually fine for public-only data.

## Profile README snippet

Add this to the `README.md` in your `colincode0/colincode0` profile repo:

```html
<picture>
  <source
    media="(prefers-color-scheme: dark)"
    srcset="https://raw.githubusercontent.com/colincode0/github-readme/main/output/contribs-dark.svg"
  />
  <img
    alt="Isometric GitHub contribution chart"
    src="https://raw.githubusercontent.com/colincode0/github-readme/main/output/contribs-light.svg"
  />
</picture>
```

## Files

- [generate_contribs.py](/Users/afx/Documents/GitHub/github-readme/generate_contribs.py): fetches GitHub data and renders the SVGs
- [.github/workflows/update-contribs.yml](/Users/afx/Documents/GitHub/github-readme/.github/workflows/update-contribs.yml): regenerates and commits the SVGs every day
- `output/contribs-light.svg` and `output/contribs-dark.svg`: created after the first local run or workflow run
