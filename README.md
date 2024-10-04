# Git intro

> [!NOTE]
> This is a short practical introduction to collaborative Git fundamentals. For the theoretical part, see the [slides](https://epflch.sharepoint.com/:p:/s/ENAC-IT/EQbIB8F9_1BIhx9TxSRGx-MBUOm4uUa-Ay5uzvb8opRO3g?e=CFzZlJ).

Go get started:
1. Create a GitHub account.
2. Fork this repository.
3. Install Git on your computer.
4. Clone your forked repository:
```bash
git clone <your-repository-url>
```

## Configuration

1. Set your name and email address.
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@something.com"
```
2. Git uses Vim as its default text editor, for example when writing commit messages. If you are not familiar with Vim, you can change the default editor to another one, for example Nano:
```bash
git config --global core.editor nano
```


## Exercise 1: Commit

1. Make a change in `file_1.md`.
2. Check the status of the repository.
```bash
git status
```
3. Check the changes made in the file.
```bash
git diff
```
4. Add the file to the staging area.
```bash
git add file_1.md
```
5. Commit the changes.
```bash
git commit -m "put a descriptive message here"
```
6. Push your local changes to the remote repository.
```bash
git push
```
7. Check the current tree of commits.
```bash
git log --all --decorate --oneline --graph
```
> [!TIP]
> Instead of typing the long `git log` command every time, you can create an alias for it (here `git lg`):
> ```bash
> git config --global alias.lg "log --all --decorate --oneline --graph"
> ```


## Exercise 2: Checkout

1. Checkout to the previous commit.
```bash
git checkout HEAD~
```
2. Git will tell you that your are now in _detached HEAD_ state, meaning that you are no longer attached to a branch. Look at the content of `file_1.md`. What do you see?
3. Check your current position in the tree of commits, indicated by `(HEAD)`.
```bash
git log --all --decorate --oneline --graph
```
4. To go back to the `main` branch, do:
```bash
git checkout main
```
5. Look at the content of `file_1.md` again. What do you see?
6. You can also checkout to a specific commit by using its hash. Look at the tree of commits (`git log`) and checkout to a previous commit.


## Exercise 3: Branch

1. Create a new branch from the commit of the previous exercise.
```bash
git branch new-branch
```
2. List all the branches.
```bash
git branch
```
3. Switch to the new branch.
```bash
git checkout new-branch
```
4. Make a change in `file_2.md`.
5. Commit your changes.
6. Look at the current tree of commits.
```bash
git log --all --decorate --oneline --graph
```

> [!TIP]
> The `git branch new-branch` and `git checkout new-branch` commands can be combined into a single command:
> ```bash
> git checkout -b new-branch
> ```

_Bonus step: Try to push `new-branch` to the remote repository (`origin`). Note that `new-branch` does not exist on the remote repository yet._


## Exercise 4: Merge

1. Make sure that all changes are commited on `new-branch`. Running `git status` should show `nothing to commit, working tree clean`.
2. Switch back to the `main` branch.
```bash
git checkout main
```
3. Merge the changes from `new-branch` to `main`.
```bash
git merge new-branch
```
4. Look at the current tree of commits.


## Bonus Exercise: Merge Conflict

1. Create a branch `conflict-branch` from `main`.
2. Make a change in `file_1.md` in `conflict-branch` and commit it.
3. Switch back to `main` and commit a different change in `file_1.md` that conflicts with the change commited in `conflict-branch` (_e.g._ change the same line).
4. Merge `conflict-branch` to `main` and resolve the conflict.


## Exercise 5: Pull Request

1. Checkout the `main` branch and push it to the remote repository.
2. Go to the GitHub page of your forked repository.
3. Create a pull request from your `main` branch to the original repository's `main` branch.
4. Add a description and comments to the pull request.


# Additional Resources

- [https://learngitbranching.js.org/](https://learngitbranching.js.org/) Git branching for beginners
- [Exercises on rewritting history](https://learngitbranching.js.org/)
- [Do you really know git?](https://rse.epfl.ch/post/2024-07-10_lightning-talks/20240710-RSE_lightning-Bryan_Perdrizat.pdf) Lightning talk from fellow EPFL RSE
