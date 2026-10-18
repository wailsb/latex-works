# How to Request Changes to a LaTeX File

This repository holds LaTeX sources (for example `init.tex`). Every change goes on its **own branch**, never directly on `main`. Follow the rules below whenever you ask for a modification, whether you ask a teammate or an AI assistant.

---

## 1. What a change request must contain

A request is complete only when it answers all four of these questions:

| # | Item | Example |
|---|------|---------|
| 1 | **File**: which `.tex` file | `init.tex` |
| 2 | **Line range**: first and last line to replace | lines `12` to `30` |
| 3 | **New content**: the exact LaTeX that replaces those lines | see the template below |
| 4 | **Branch**: the name of the new branch | `wailsb/fix-intro-section` |

If any item is missing, the request is ambiguous and should be sent back for clarification.

---

## 2. Request template

Copy this, fill in the blanks, and send it:

````text
I want to make these modifications to <file>.tex from line __ to line __.
Check out a new branch named <username>/<description>, apply the changes,
replace those lines with the LaTeX below, then commit and push to that branch.

Commit message: "<what changed>"

New LaTeX:
```latex
% paste the replacement LaTeX here
```
````

### Filled-in example

````text
I want to make these modifications to init.tex from line 12 to line 18.
Check out a new branch named wailsb/rewrite-abstract, apply the changes,
replace those lines with the LaTeX below, then commit and push to that branch.

Commit message: "Rewrite abstract to be shorter"

New LaTeX:
```latex
\begin{abstract}
This document presents a concise overview of ...
\end{abstract}
```
````

---

## 3. Rules

1. **One request = one branch = one topic.** Don't mix unrelated edits on the same branch.
2. **Line numbers refer to the current `main`.** Check them on an up-to-date copy before sending the request.
3. **The line range is inclusive.** "Line 12 to line 18" replaces lines 12 through 18, both ends included.
4. **Give the full replacement text.** Don't describe it ("make it shorter"). Paste the exact LaTeX that should end up in the file.
5. **Keep LaTeX valid.** Every `\begin{...}` needs its `\end{...}`, and braces `{}` must be balanced inside the range you replace.
6. **Branch names use a forward slash** (`/`), not a backslash (`\`). Git treats `\` badly, especially on Windows.
7. **Commit messages say *what* changed**, in the present tense (e.g. `Fix typo in section 2 title`).
8. **Never push directly to `main`.** Changes reach `main` only through a pull request.

---

## 4. Branch naming

```
<username>/<description>
```

- `username`: your GitHub username (e.g. `wailsb`)
- `description`: short, lowercase, words joined with hyphens

| Good | Bad |
|------|-----|
| `wailsb/fix-table-caption` | `wailsb\fix table caption` |
| `wailsb/add-references` | `changes` |
| `wailsb/rewrite-abstract` | `Wailsb/Rewrite_Abstract!!` |

---

## 5. Git commands for applying a request

```bash
# 1. Start from an up-to-date main
git checkout main
git pull

# 2. Create and switch to the new branch
git checkout -b <username>/<description>

# 3. Edit the .tex file: replace lines __ to __ with the new LaTeX

# 4. Stage, commit, and push
git add .
git commit -m "what changed"
git push -u origin <username>/<description>
```

> **Note:** the first push of a new branch needs `-u origin <branch-name>`. A bare `git push` fails because the branch doesn't exist on GitHub yet. After the first push, a plain `git push` works.

---

## 6. After pushing

1. Open the repository on GitHub: <https://github.com/wailsb/latex-works>
2. Click **Compare & pull request** for your branch.
3. Describe the change and open the pull request into `main`.
4. Once it's reviewed and merged, delete the branch.
