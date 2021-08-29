---
layout: post
title:  "Rebase Squash"
date:   2021-08-29 07:58:00 -0700
categories: adv-git
---
What is the squash rebase workflow?
It’s simple – before you merge a feature branch back into your main branch (often master or develop), your feature branch should be squashed down to a single buildable commit, and then rebased from the up-to-date main branch. Here’s a breakdown.


Pull master branch

`git pull origin master`

Create bug/feature branch

`git checkout -b branchName`

Make changes as needed with as many commits that you need to. Make sure the final commit is buildable and all tests pass.

Get the number of commits from the start of your branch. There are a couple of ways to get this. You can simply git log and count your commits, or

`git log --graph --decorate --pretty=oneline --abbrev-commit`

which will show a graph of your commit log history and may be easier to visualize your commits. Sometimes you will have large enough number of commits that counting can become troublesome. In that case grab the SHA from the last commit that your branch branches from.

Squash to 1 commit.

`git rebase -i HEAD~[NUMBER OF COMMITS]`

OR

`git rebase -i [SHA]`

If you have previously pushed your code to a remote branch, you will need to force push.

`git push origin branchName --force`

Checkout master branch

`git checkout master`

Pull master branch

`git pull origin master`

Checkout bug/feature branch

git checkout branchName

Rebase from master

`git rebase master`

Handle any conflicts and make sure your code builds and all tests pass. Force push branch to remote.

`git push origin branchName --force`

Checkout, merge, and push into master

`git checkout master`

git merge branchName

`git push origin master`


## References:

1. [ Always Squash and Rebase your Git Commit ](https://blog.carbonfive.com/always-squash-and-rebase-your-git-commits/)