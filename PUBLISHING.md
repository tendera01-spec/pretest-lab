# Publishing Guide

Steps to take Pretest Lab from the Vault to a public GitHub repo and onto LinkedIn.

All placeholders are filled in for `tendera01-spec/pretest-lab`. Just copy, init, push.

## 1. Rename existing GitHub repo (if `ad-pretest` is already there)

If you already created `tendera01-spec/ad-pretest` earlier, rename it on GitHub first. GitHub keeps an automatic redirect from the old name.

```bash
gh repo rename pretest-lab --repo tendera01-spec/ad-pretest
```

If no old repo exists yet, skip this step.

## 2. Push to GitHub

```bash
# Local copy out of the Vault
mkdir -p ~/Dev
rm -rf ~/Dev/pretest-lab 2>/dev/null
cp -R "/Users/gregormyszor/Obsidian/Obsidian Vault 2/04_Ops/Marketing/oss-skills/pretest-lab" ~/Dev/pretest-lab
cd ~/Dev/pretest-lab

# Init Git
git init -b main
git add .
git commit -m "Initial release v1.1.0

Pretest Lab. A pre-launch quality gate for design and communication assets.
Pretest pitch decks, landing pages, LinkedIn posts, ads, CVs and any visual asset before it ships.
Limbic archetypes, Decoded neuromarketing, Creative Expert Roundtable (12 lenses), A/B comparison.
From the Creative Intelligence System.
EN primary, DE bonus."
```

If the repo doesn't exist yet on GitHub:

```bash
gh repo create pretest-lab \
  --public \
  --source=. \
  --remote=origin \
  --description "A pre-launch quality gate for design and communication assets. Pretest pitch decks, landing pages, LinkedIn posts, ads, CVs and any visual asset before it ships. Built on the Limbic Model, Decoded neuromarketing and a 12-lens Creative Expert Roundtable. From the Creative Intelligence System." \
  --push
```

If the repo already exists (after rename):

```bash
git remote add origin https://github.com/tendera01-spec/pretest-lab.git
git push -u origin main --force
```

## 3. Tag the Release

```bash
git tag -a v1.1.0 -m "v1.1.0 initial public release"
git push origin v1.1.0

gh release create v1.1.0 \
  --title "v1.1.0 Pretest Lab" \
  --notes-file CHANGELOG.md

gh repo view --web
```

## 4. Repo Polish

On the GitHub repo page:

- **About** sidebar: add website `https://www.gregoradammyszor.com`, add topics (pretest, quality-gate, communication-design, limbic-model, neuromarketing, claude-code, pitch-deck).
- **Social preview image**: upload `assets/linkedin-cover.png` (Settings → General → Social preview).
- **Pin the repo** on the GitHub profile.

## 5. LinkedIn Post

Draft in `04_Ops/Marketing/linkedin/pretest-lab-launch.md`. Three versions ready.

1. Pick Version A (long) or B (short)
2. Attach `assets/linkedin-cover.png` as the post image
3. Post the prepared first comment from the checklist
4. First 30 minutes: respond to comments quickly

## 6. Post-Launch Tracking

- Pin the repo on the GitHub profile
- Add the repo to LinkedIn Featured
- Track stars, issues, forks weekly
- Track gregoradammyszor.com referral spike
- If 20+ reactions on LinkedIn: second-wave post in 7 to 10 days
- If 50+ stars in week 1: blog post on gregoradammyszor.com tying Pretest Lab to the Creative Intelligence System

## 7. Roadmap

- **v1.2** Multi-market Limbic distributions (UK, US, FR, NL)
- **v1.3** Video and animated asset support
- **v1.4** Brand consistency scoring against uploaded brand foundation PDF
- **v1.5** Deck-specific mode: slide-by-slide flow analysis
