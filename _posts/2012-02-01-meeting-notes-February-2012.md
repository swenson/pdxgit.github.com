---
layout: article
category: meetings
title: "Meeting Notes: February 2012 at Collective Agency"
---

## git 1.7.x

* submodules suck less
* multi-cherry-pick
* sparse checkout
* `git grep` is multithreaded
* `git-svn` groks svn merges (!!!)
* `git stash` corner cases fixed (???)
	- index item
* general gitweb improves
	- code hilite
* sugar for delete branch
	- `git push origin :goner` #old syntax to push "nothing"
	- now: `git push origin --delete goner`
* new diff algorithm "patience"
* `git merge --edit` : instead of `--nocommit` to do a merge with an altered commit msg
* `git submodule update --inint --recursive` # rec is a new opt to do what you think 
	- meta data has been shifted from external dirs to the core .git dir so that git now knows where to find everything and do the right thing at the right time because of this

## libgit2

* a magical world
* reimplement git
* like kid sister, not a fork or replacement, shares API
* attempts to fix issues that are baked in to git 1.x for not being a lib 
* progable, native win support
* ligher footprint, better for embeded/mobile
	- direct func calls to repo, less overhead when compaired to CLI toolkit
* [http://libgit2.github.com](http://libgit2.github.com)
	- github and GSoC history, github has plans to use in prod though status is unknown at this time
* what can you do currently? 
	- open repos
	- look into repos
	- create commits, search commits
* what is not yet possible
	- no remote access thus push and pull are not yet working
* repo: [https://github.com/libgit2](https://github.com/libgit2)
	- \#libgit2 on irc.freenode 
	- libgit2@librealist.com #mailinglist
* how to help? 
	- need test to be written
	- contact and see what else can help

## Meta: how to get involved with pdxgit? 

* [https://github.com/pdxgit](https://github.com/pdxgit)
* [http://pdxgit.com](http://pdxgit.com) (will fix soon)
* pdxgit@librelist.com #mailinglist
* propose a meeting topic or give a talk
* Collective Agency is awesome, support them it's cheap!

## QA Sessions

* what about `git-flow`?
	- seems over engineered
		- why are there dev, release and hotfix branches?
			- you can add them later if you *really* need them
	- it's overkill for 99% of general products 
		- work-flow is really based on the boxed software model 
		- if you just have a 'webapp' where current is always live then it's kinda bunk
	- git is an **extremely** flexible tool so you can look at your flow and then mold the use of the tool to the team, no need to go the extra mile and force a new flow on a team just because of a tool. 
	- the good thing is that the `git-flow` command wraps up common patterns
		- but it does hide what's going on and so when something blows up then what *really* happended as it's all hidden
* read [commit #1](https://github.com/gitster/git/commit/e83c5163316f89bfbde7d9ab23ca2e25604af290) from git://github.com/gitster/git.git it's enlightening
* how to take an untracked project, but you have a dev and prod dir that should be branches
	- `cd prod` -> `git init` -> `git add` -> `git ci` -> `git tag`
	- `git co -b dev` -> `del *` -> `cp -rv ../dev/* .` -> `git st` -> `git add` -> `git tag`
* `svn loaddirs` ... how do you do something like this in git? 
	- same as above whipe out working copy, cp new files, st to check, add *, ci, tag
