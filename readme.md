### A. Create a New Git Repository and clone it for use it.

```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises
$ cd 'c:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository'

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git checkout -b dev
Switched to a new branch 'dev'
        
```

### B. Initialize Your Environment : By creating 4 md.files and add some comments.
##### touch test{1..4}.md
```bash
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"
```
```bash
On branch dev
nothing to commit, working tree clean
On branch dev
nothing to commit, working tree clean
On branch dev
nothing to commit, working tree clean
```
## Part 1: Refining Git History
 ##### 1.Missing File Fix:
  Here I check repo state, notice test4.md missing, then stage it and amend last commit with proper message.  
 ```bash
 user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git add test4.md

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git commit --amend -m "chore: Create third and fourth files"
[dev ff4bd50] chore: Create third and fourth files
 Date: Thu Oct 2 18:06:33 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
ff4bd50 (HEAD -> dev) chore: Create third and fourth files
c1ab859 chore: Create another file
f6cf2a2 chore: Create initial file

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git show HEAD --name-only
commit ff4bd507603228709fcd6fcf528a61a8fdd8bbd3 (HEAD -> dev)
Author: samuel-ishimwe203 <samuelishimw02@gmail.com>
Date:   Thu Oct 2 18:06:33 2025 +0200

    chore: Create third and fourth files

test3.md
test4.md
 ```

##### 2. Editing Commit History:
   here I update commit message from 'Create another file' to 'Create second file' using interactive rebase for clarity
   
 ```bash
 user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git rebase -i HEAD~2
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to Unix format...
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/COMMIT_EDITMSG to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/COMMIT_EDITMSG to Unix format...
[detached HEAD 69da35f] chore: Create second file
Date: Thu Oct 2 18:06:20 2025 +0200
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100644 test2.md
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/COMMIT_EDITMSG to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/COMMIT_EDITMSG to Unix format...
[detached HEAD a8d4382] chore: Create third and fourth files
Date: Thu Oct 2 18:06:33 2025 +0200
2 files changed, 0 insertions(+), 0 deletions(-)
create mode 100644 test3.md
create mode 100644 test4.md
Successfully rebased and updated refs/heads/dev.


user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
a8d4382 (HEAD -> dev) chore: Create third and fourth files
69da35f chore: Create second file
f6cf2a2 chore: Create initial file


user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log
commit a8d4382643bb7a0e764036c0942a5fb52c4bf5d8 (HEAD -> dev)
Author: samuel-ishimwe203 <samuelishimw02@gmail.com>
Date:   Thu Oct 2 18:06:33 2025 +0200

chore: Create third and fourth files

commit 69da35f53ba3aa0355163c9e7173c0a087152dae
Author: samuel-ishimwe203 <samuelishimw02@gmail.com>
Date:   Thu Oct 2 18:06:20 2025 +0200

chore: Create second file

commit f6cf2a28cfc73f4b403eef6850151ed4fab45a55
Author: samuel-ishimwe203 <samuelishimw02@gmail.com>
Date:   Thu Oct 2 18:06:09 2025 +0200

chore: Create initial file
 
 ```
 #### 3. Keeping History Tidy - Squashing Commits:

```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git rebase -i --root
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to Unix format...
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/COMMIT_EDITMSG to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/COMMIT_EDITMSG to Unix format...
[detached HEAD b3711ea] chore: Create initial and second file
Date: Thu Oct 2 18:06:09 2025 +0200
2 files changed, 0 insertions(+), 0 deletions(-)
create mode 100644 test1.md
create mode 100644 test2.md
Successfully rebased and updated refs/heads/dev.

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
c3b9f5a (HEAD -> dev) chore: Create third and fourth files
b3711ea chore: Create initial and second file

``` 
#### 4. Splitting a Commit:
Here also i split 'Create third and fourth files' into two commits using git reset for clearer messages.
```bash 
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git status
On branch dev
Your branch and 'origin/dev' have diverged,
and have 1 and 3 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   test3.md
        new file:   test4.md
Untracked files:
(use "git add <file>..." to include in what will be committed)
        readme.md

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git reset

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git add test3.md
git commit -m "chore: Create Third File"
[dev 045fe16] chore: Create Third File
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git add test4.md
git commit -m "chore: Create Fourth File"
[dev 10007a3] chore: Create Fourth File
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
10007a3 (HEAD -> dev) chore: Create Fourth File
045fe16 chore: Create Third File
b3711ea chore: Create initial and second file

```
#### 5.Advanced Squashing:
Here I Squash the last two commits into one named 'Create third and fourth files' using interactive rebase.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git rebase -i HEAD~2
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to Unix format...
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/COMMIT_EDITMSG to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/COMMIT_EDITMSG to Unix format...
[detached HEAD 887abaf] chore: Create third and fourth files
 Date: Thu Oct 2 19:29:27 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/dev.

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
887abaf (HEAD -> dev) chore: Create third and fourth files
b3711ea chore: Create initial and second file

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git push origin dev --force
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 447 bytes | 447.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/samuel-ishimwe203/Git-Exercise-Repository.git
 + a8d4382...887abaf dev -> dev (forced update)
```
#### 6.Dropping a Commit:
Remove an unwanted commit ('Unwanted commit') from history using git rebase -i.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ touch unwanted.txt

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git add unwanted.txt
git commit -m "Unwanted commit"
[dev be7378d] Unwanted commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 unwanted.txt

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
be7378d (HEAD -> dev) Unwanted commit
887abaf (origin/dev) chore: Create third and fourth files
b3711ea chore: Create initial and second file

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git rebase -i HEAD~1
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to Unix format...
Successfully rebased and updated refs/heads/dev.

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
887abaf (HEAD -> dev, origin/dev) chore: Create third and fourth files
b3711ea chore: Create initial and second file
```
#### 7. Reordering Commits:
 Here I am going to reorder commits in history using git rebase -i
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
887abaf (HEAD -> dev, origin/dev) chore: Create third and fourth files
b3711ea chore: Create initial and second file

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git rebase -i --root
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to DOS format...
dos2unix: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/rebase-merge/git-rebase-todo to Unix format...
Successfully rebased and updated refs/heads/dev.

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git log --oneline
1221eea (HEAD -> dev) chore: Create initial and second file
843be08 chore: Create third and fourth files
```
#### 8. Cherry-Picking Commits:
Here I use git cherry-pick to bring a specific commit from ft/branch into main.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git checkout main
Switched to branch 'main'
Your branch is behind 'origin/main' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git checkout -b ft/branch
Switched to a new branch 'ft/branch'

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/branch)
$ echo "This is test 5 content" > test5.md
git add test5.md
git commit -m "Implemented test 5"
warning: in the working copy of 'test5.md', LF will be replaced by CRLF the next time Git touches it
[ft/branch ac9a27e] Implemented test 5
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/branch)
$ git log --oneline
ac9a27e (HEAD -> ft/branch) Implemented test 5
c1ab859 (main) chore: Create another file
f6cf2a2 chore: Create initial file

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/branch)
$ git checkout main
Switched to branch 'main'
Your branch is behind 'origin/main' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/clGit-Exercise-Repository (main)
$ git cherry-pick ac9a27e
[main 18a1edf] Implemented test 5
 Date: Thu Oct 2 20:03:57 2025 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md
```
#### 9. Visualizing Commit History (Bonus):
Here is git log --graph or a Git client to visualize commit history.
```bash 
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git log --oneline --graph --all --decorate
* 18a1edf (HEAD -> main) Implemented test 5
| * ac9a27e (ft/branch) Implemented test 5
|/
| * 1221eea (dev) chore: Create initial and second file
| * 843be08 chore: Create third and fourth files
| * 887abaf (origin/dev) chore: Create third and fourth files
| * b3711ea chore: Create initial and second file
| * 452901e (origin/main) all
| * 16b9abb chore: Create third and fourth files
|/
* c1ab859 chore: Create another file
* f6cf2a2 chore: Create initial file
```
#### 10. Understanding Reflogs (Bonus):
Here I show git reflog to track operations and return to previous states.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git reflog
18a1edf (HEAD -> main) HEAD@{0}: cherry-pick: Implemented test 5
c1ab859 HEAD@{1}: checkout: moving from ft/branch to main
ac9a27e (ft/branch) HEAD@{2}: commit: Implemented test 5
c1ab859 HEAD@{3}: checkout: moving from main to ft/branch
c1ab859 HEAD@{4}: checkout: moving from dev to main
1221eea (dev) HEAD@{5}: rebase (finish): returning to refs/heads/dev
1221eea (dev) HEAD@{6}: rebase (pick): chore: Create initial and second file
843be08 HEAD@{7}: rebase (pick): chore: Create third and fourth files
ecd7fdd HEAD@{8}: rebase (start): checkout ecd7fdd3979ea762b18bfad06975fb60123b9e44
887abaf (origin/dev) HEAD@{9}: rebase (finish): returning to refs/heads/dev
887abaf (origin/dev) HEAD@{10}: rebase: fast-forward
b3711ea HEAD@{11}: rebase: fast-forward
14e22d6 HEAD@{12}: rebase (start): checkout 14e22d6e3b61fccd2176135481da04d8f063d565
887abaf (origin/dev) HEAD@{13}: rebase (finish): returning to refs/heads/dev
887abaf (origin/dev) HEAD@{14}: rebase (start): checkout HEAD~1
887abaf (origin/dev) HEAD@{15}: rebase (finish): returning to refs/heads/dev
887abaf (origin/dev) HEAD@{16}: rebase (start): checkout HEAD~1

```


## Part 2: Branching Basics (10 Challenges)
#### 1. Feature Branch Creation:
Here I create and switch to a new branch named ft/new-feature
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git checkout dev
Switched to branch 'dev'
Your branch and 'origin/dev' have diverged,
and have 2 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (dev)
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git branch
  dev
  ft/branch
* ft/new-feature
  main
```
#### 2.Working on the Feature Branch:
Here I add feature.txt with content and commit as 'Implemented core functionality for new feature'.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ echo "This is the core functionality of the new feature" > feature.txt

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git add feature.txt
warning: in the working copy of 'feature.txt', LF will be replaced by CRLF the next time Git touches it

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature 411deb7] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txtcd 

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git log --oneline
411deb7 (HEAD -> ft/new-feature) Implemented core functionality for new feature
1221eea (dev) chore: Create initial and second file
843be08 chore: Create third and fourth files

```
#### 3. Switching Back and Making More Changes:
Here I switch to main branch, add readme.txt, and commit as 'Updated project readme'.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git checkout main
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 1 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ echo "This is the project readme with introductory content" > readme.txt

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git commit -m "Updated project readme"
[main f1927ab] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git log --oneline
f1927ab (HEAD -> main) Updated project readme
18a1edf Implemented test 5
c1ab859 chore: Create another file
f6cf2a2 chore: Create initial file

```
#### 4. Local vs. Remote Branches:
Here also learn about remote branches and how to push/pull to keep them in sync with local branches.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git branch
  dev
  ft/branch
  ft/new-feature
* main

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git push -u origin ft/new-feature
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 16 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (8/8), 725 bytes | 725.00 KiB/s, done.
Total 8 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), done.
remote:
remote: Create a pull request for 'ft/new-feature' on GitHub by visiting:
remote:      https://github.com/samuel-ishimwe203/Git-Exercise-Repository/pull/new/ft/new-feature
remote:
To https://github.com/samuel-ishimwe203/Git-Exercise-Repository.git
 * [new branch]      ft/new-feature -> ft/new-feature
branch 'ft/new-feature' set up to track 'origin/ft/new-feature'.

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git pull origin main
From https://github.com/samuel-ishimwe203/Git-Exercise-Repository
 * branch            main       -> FETCH_HEAD
hint: Waiting for your editor to close the file... unix2dos: converting file C:/Users/user/Desktop/Git-Exercises/Git-Exercise-Repository/.git/MERGE_MSG to DOS format...


user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main|MERGING)
$ git branch -a
  dev
  ft/branch
  ft/new-feature
* main
  remotes/origin/dev
  remotes/origin/ft/new-feature
  remotes/origin/main
```
#### 5. Branch Deletion:
Here I want to delete ft/new-feature branch after merging into main.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main|MERGING)
$ git checkout main
D       test1.md
D       test2.md
Already on 'main'
Your branch and 'origin/main' have diverged,
and have 2 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git branch
  dev
  ft/branch
  ft/new-feature
* main

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git branch -d ft/new-feature
warning: deleting branch 'ft/new-feature' that has been merged to
         'refs/remotes/origin/ft/new-feature', but not yet merged to HEAD
Deleted branch ft/new-feature (was 411deb7).

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git branch
  dev
  ft/branch
* main
```
#### 6. Creating a Branch from a Commit:
Here I have create a branch from a specific commit using git checkout -b ft/new-branch-from-commit <commit-hash>.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git log --oneline
f1927ab (HEAD -> main) Updated project readme
18a1edf Implemented test 5
c1ab859 chore: Create another file
f6cf2a2 chore: Create initial file

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git checkout -b ft/new-branch-from-commit f6cf2a2
D       test1.md
Switched to a new branch 'ft/new-branch-from-commit'

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-branch-from-commit)
$ git branch
  dev
  ft/branch
* ft/new-branch-from-commit
  main

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-branch-from-commit)
$ git log --oneline
f6cf2a2 (HEAD -> ft/new-branch-from-commit) chore: Create initial file

```
#### 7. Branch Merging:
Here I merge ft/new-branch-from-commit into main and resolve any conflicts.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git branch
  dev
  ft/branch
  ft/new-branch-from-commit
* main

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git merge ft/new-branch-from-commit
Already up to date.

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (main)
$ git log --oneline --graph --all
* f1927ab (HEAD -> main) Updated project readme
* 18a1edf Implemented test 5
| * 411deb7 (origin/ft/new-feature) Implemented core functionality for new feature
| * 1221eea (dev) chore: Create initial and second file
| * 843be08 chore: Create third and fourth files
| * ac9a27e (ft/branch) Implemented test 5
|/
| * 887abaf (origin/dev) chore: Create third and fourth files
| * b3711ea chore: Create initial and second file
| * 452901e (origin/main) all
| * 16b9abb chore: Create third and fourth files
|/
* c1ab859 chore: Create another file
* f6cf2a2 (ft/new-branch-from-commit) chore: Create initial file
```
#### 8 . Branch Rebasing:
Here I merge ft/new-branch-from-commit into main and resolve any conflicts.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git status
On branch ft/new-feature
Your branch and 'origin/ft/new-feature' have diverged,
and have 6 and 3 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    test1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        readme.md

no changes added to commit (use "git add" and/or "git commit -a")

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git add .
git commit -m "Save work before rebase"
[ft/new-feature 28c9d6f] Save work before rebase
 2 files changed, 557 insertions(+)
 create mode 100644 readme.md
 delete mode 100644 test1.md

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git stash
No local changes to save

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git rebase main
Current branch ft/new-feature is up to date.

```
#### 9. Renaming Branches:
Here I rename branch ft/new-branch-from-commit to ft/improved-branch-name using git branch -m.
``` bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git branch
  dev
  ft/branch
  ft/new-branch-from-commit
* ft/new-feature
  main

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git branch -m ft/new-branch-from-commit ft/improved-branch-name

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git branch
  dev
  ft/branch
  ft/improved-branch-name
* ft/new-feature
  main

```
#### 10. Checking Out Detached HEAD:
Here I used git checkout <commit-hash> to enter a detached HEAD state.
```bash
user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git log --oneline --graph
* 28c9d6f (HEAD -> ft/new-feature) Save work before rebase
* 33f9b66 Implemented core functionality for new feature
* 0357902 chore: Create third and fourth files
* f1927ab (main) Updated project readme
* 18a1edf Implemented test 5
* c1ab859 chore: Create another file
* f6cf2a2 (ft/improved-branch-name) chore: Create initial file


user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git add readme.md
git commit -m "Save changes before checkout"
[ft/new-feature 8c0ab1c] Save changes before checkout
 1 file changed, 61 insertions(+)

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/new-feature)
$ git checkout f6cf2a2
Note: switching to 'f6cf2a2'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at f6cf2a2 chore: Create initial file


user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository ((f6cf2a2...))
$ git checkout f6cf2a2
HEAD is now at f6cf2a2 chore: Create initial file

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository ((f6cf2a2...))
$ git checkout -b ft/experiment
Switched to a new branch 'ft/experiment'

user@LAPTOP-7PT2H9GQ MINGW64 ~/Desktop/Git-Exercises/Git-Exercise-Repository (ft/experiment)
$ git checkout main
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 2 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

```

## Advanced Workflows (10+ Challenges)
#### 1. Stashing Changes:
Here I use git stash to save uncommitted changes temporarily in main.
```bash


```