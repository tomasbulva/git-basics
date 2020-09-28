# intro by Margherita
In my experience, one of my nightmares was Git. I wished I had some knowledge before starting messing up with the repositories. Git is a tool for developers to write a piece of code altogether.
You can imagine that 5+ hands on the same code can create quite a mess, if not handled. Git allows to do version-control, and each developer can branch out from the main code and do their mess there, minimising the conflict between two people working on the same project, but on different files. First, you’ll need to store that code remotely in a repository (meaning: on some web hosts, such as GitLab or GitHub). In the new branch, the developer will have all the original code, the latest version that has been pulled, and she can start coding down her own features. Once she has a stable working feature, she can commit those changes and then continue working, maybe do other commits. Once she’s done, she will push it remotely, creating a copy of the local branch on the same repository that hosts the main code. Before allowing any random branch simply merge into the original main code, the developer has to open a merge request (or pull request, depends on whether you are on GitLab or GitHub – you’ll probably hear the second one more often, as we work on GitHub). When the merge request is open, the rest of the team can access to a remote copy of the developer branch and give feedback on lines of the code and discuss the implementation. Or, if you’re lucky, directly approve it to be merged.
Of course this is simplistic (even though seems a lot already!) and there’s a world behind it, but I hope it explains you why a team of developers relies so much on it. As you see, just by chatting about Git, I came up with a lot of terms that are for sure new to you (all the italic ones – typical Git slang).
Here there’s a fun git-based game that Nico gave me before I joined. It can help you familiarise with words you’ll hear on a daily basis.


## Links and tools:
- (git flow)[https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow]
- (learngitbranching)[https://learngitbranching.js.org/] -- It’s a great tool, but indeed it makes struggle most of us at the beginning.
- [git log --graph](https://elsevier-scopus.slack.com/archives/D01BL8H7XR7/p1601021342000200)
- [zine pdf](https://elsevier.enterprise.slack.com/files/WN1VDAZ0R/F01BDR3VDK6/dangit-git-zine.pdf)
- [cheetsheet](https://elsevier-scopus.slack.com/archives/D01BL8H7XR7/p1601022431000600)
- [tig](https://jonas.github.io/tig/INSTALL.html#_installation_using_homebrew)
- [ohmyzsh](https://github.com/ohmyzsh/ohmyzsh)


# branches
  ...explanation

# what is github good for
- `git format-patch master --stdout > fix_empty_poster.patch`
- (pull requests)[https://github.com/tomasbulva/git-basics/pulls]


# basic work
  ```bash
  mkdir project-name
  cd project-name
  git init -> create master by default

  touch my-amazing-code.js

  git add my-amazing-code.js || git add . || git add -A

  git commit -m "my commit/update/feature description"

  commit SHA token
  commit position HEAD
  ```
  // for ssh (should we talk about the difference between remote repository communication protocols?)
  `git remote add origin git@github.com:repository-owner-name/repository-name.git`

  // for https
  `https://github.com/repository-owner-name/repository-name.git`

  git push origin master

# logs

  1. `git log`

  2. `git log --graph --oneline --all`

  3. `tig`

# work with code other made
  - `fetch`
  - `pull`

# work with your code on top of others
  - `git status`
  - `git diff HEAD filename.js`

# basic fixes
  ```bash
  # undoing adds
  # if not commited
  git restore filename
  git checkout filename

  # if commited
  git restore --staged filename && git restore filename

  # if you need to add to previous commit
  git commit --amend -no-edit
  ```

  continue or abort

  `git merge --contine`
  `git merge --abort`

  `git rebase --continue`
  `git rebase --abort`

# advanced
  ```bash
  git config --global init.defaultBranch {branchName}

  git reset --soft SHA

  ###!!!!!!!!!!!###
  git reset --hard SHA
  ### this will delete everything permanently
  ###!!!!!!!!!!!###

  git pull origin master
  git checkout feature-branch
  git rebase master
  ```

# how to manage rebase from hell
  ```bash
  git rebase --abort
  git reset --soft SHA // my changes starting
  git stash
  git merge master
  git stash pop

  # practice stash hygiene
  git stash list
  ```

# how to make sense of my git settings
  all git magic happens in the .git folder
  `atom .git/config`

# how to delete BRANCHES
## local branch
  - `git branch -d local-branch-name`
  - `git branch -D local-branch-name #force delete`

## delete remote branch
  - `git push origin --delete remote-branch-name`

# get the scoop
 - `git annotate -- path/filename`
 - `git blame -- path/filename`

# cherry picking
  will bring specific commit from one branch to other branch
  get the hash you want to bring.
  cherry pick from the destination branch

  - `git cherry-pick SHA`
  - `git cherry-pick SHA SHA SHA`

  - `git cherry-pick --continue`
  - `git cherry-pick --abort`

# productivity
## set aliases
  .bashrc or .zshrc
  - `alias gm="git commit -m "`

## oh my zsh
  [oh my zsh git cheatsheet](https://github.com/ohmyzsh/ohmyzsh/wiki/Cheatsheet)
