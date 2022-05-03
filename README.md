# GIT

# Version Controlling
=====================
This is the process of preserving older and latest
versions of the code.
All the developers upload their code into the
VCS.The VCS's accept the code uploads coming from
various developers and create one integrated project
out of those uploads.
The next time when developers download the code
from the VCS they will find the code created by the
entire team.Process of uploading into VCS is called 
"cehckin" and downloading from VCS is called "checkout"


VCS's also preserve the different versions of the code
so that the developers can swithc between any version
based on requirement.

VCS's also track who is making what kind of changes

VCS's are of two types
1 Centralised Version Controlling
2 Distributred Version Controlling

# Centralised Version Controlling
---------------------------------
	Here we have a remote server where version
controlling happens.All the developers checkin their
code into this central server.
Eg: SVN(SubVersion)

# Distributred Version Controlling
-----------------------------------
	Here a local repository is installed on every
developers machine where version controlling happens
at the level of the individual developer.Later from
the LR the code is uploaded to the remote repository
where version controlling happens at the level of the
complete team.


# Installing git on windows
=============================
1 Open https://git-scm.com/downloads
2 Download git for windows--->Install it
3 Open git bash
4 Execute the git commands

# Installing git on a Linux(Ubuntu)
======================================
1 Update the apt-repository
  sudo apt-get update
2 Install git
  sudo apt-get install -y git

To check the version of git
git --verion

Setting username and email globally for all users
git config --global user.name "sai krishna"
git config --global user.email "sai@gmail.com"

To see the list of all default configuration
git config --global --list

# DAY 2

Git when working on the local machine uses three
sections.
1 Working directory(workspace)
2 Stagging Area
3 Local Repository

Working directory
--------------------
	Initially all the files created by the 
developers are stroed in a folder called working
directory and these files are initially called
untracked files.

Stagging Area
---------------
	Files from working directory are moved to
an intermediate memory area called stagging area.
The files present here are called stagged files.

Local Repository
------------------
	All files from stagging area will be moved
into the local repository and this is where version
controlling happens.These files are called commited
 files

1 To initilise the working dir to accept git commands
  Open git bash
  cd path_of_working_dir
  git init
  The above command will create a hidden folder called
  .git where it stores some configuration files for 
  maintianing the local repository

2 To send file from working dir to stagging area
  git add filename
  To send multiple files into stagging area
  git add file1 file2 file3
  To send all files and fodlers into the stagging area
  git add .
  Note  . represents present working directory

3 To unstage files ie bring files back from stagging
  to untracked section
  git rm --cached filename
  (or)
  git reset filename

4 To send files from stagging to local repository
  git commit -m "Some commit message"

5 To see the status of the untracked and stagging section
  git status

6 To see the total commits that are done in LR
  git log
  To see the commit history in a simplified format
  git log --oneline


.gitignore
-------------
This is a special file where we can store the
private filenames.Any filename that is mentioned 
in .gitignore will not longer be accessed by git

1 Create few files
  touch file1 file2 file3 file4

2 Check the status of git
  git status
  It will show all the above 4 files as untracked file

3 Create a hidden file .gitignore and enter the above filenames
  cat > .gitignore
  file1
  file2
  file3
  file4
  To come out of cat command press ctrl+d (EOF)

4 Check the status of git
  git status
  It will not longer show the above created four files
  as untracked
  
  # DAY 3
  
  Git Branching
====================
	This is a feature of git using which the developers
can create seperate functionalities of code on different branches and later merge them with the master branch.This will help in creating the code in an unclutterred way

1 To see the list of all branches
  git branch
  To see all branches(local and remote)
  git branch -a

2 To create a branch
  git branch branchname

3 To move into a branch
  git checkout branchname

4 To create a branch and also move into it
  git checkout -b branchname

5 To merge a brnach with master
  First move to master
  git checkout master
  git merge branchname

6 To delete a branch that is merged
  git branch -d branchname
  This is also called soft delete

7 To delete a branch that is not merged
  git branch -D branchname
  This is also called hard delete


note: whenever a branch is created whatever is the commit history of the parent branch will be copied to the newly created branch

note: Irrespective of where a file is created or modified that file belongs to that branch form where it is commited


# Day 4

3 KB
Location
GIT
Owner
IntelliQ IT
Modified
12-Oct-2021 by IntelliQ IT
Opened
1:14 pm by me
Created
12-Oct-2021
No description
Viewers can download

Working on Git remote repository("github")
1 Open github.com
2 Signup for a free account
3 Signin into that account

To push the code from the local repository to remote repository
================================================================1 Signin into github.com
2 Click on + on top right corner
3 click on New repository
4 give some name for repository
5 Select public--->Click on Create repository
6 Go to "Push an exisiting repository from command line"
7 Copy the 1st command and paste in gitbash
  This will create a link between the local repository
  and the remote repository
8 Copy the second command and paste in gitbash
  Enter username and password of github
This process is called checkin




Downloading from remote git repository
---------------------------------------
This can be done in 3 ways
1 git clone
2 git fetch
3 git pull

git clone: This will download the entire remote repository
from git hub into individual developers machine irresepective of whether that code is already present or not
Syntax
  git clone remote_repo_url

git fetch: This will work only when there are modifications in the code between the local repository and remote repository
git fetch will download the modified files and place them on a remote branch.We can go to that remote branch check if those changes are accptable or not and if they are acceptable we can merge them with master

1 Create some modifications to any file on github
  Open github.com
  Click on our remote repository
  click on any file that we want to modify
  Click on Edit icon
  Make some changes--->click on commit changes

2 In git bash
  git fetch

3 Check the modified file on master branch
  We will not see any modifications

4 The modifications will be on the remote branch
  Move to the remote branch
  git branch -a
  git checkout -b remotes/origin/master

5 View the modified file
  If the changes are accpetable merge with master
  git checkout master
  git merge remotes/origin/master


git pull:This will also work only when there are modifications
between the local repository and the remote repository.But it will directly merge the modified files with master branch

1 Open github.com
2 Make some changes to a file--->commit changes
3 In git bash
  git pull
The modified files can be directly seen on the master


172.31.84.215
172.31.87.185
172.31.87.143


# Day 5


git merge and git rebase
=============================
git merge: In git merge the commits are inserted into the branch that we are merging exactly at the location that they were 
created.which means the commits coming from a branch can look like older commits on the master

1 On the master create few commits
touch f1
git add .
git commit -m "a"
touch f2
git add .
git commit -m "b"

2 Create a new branch and create few commits on it
  git checkout -b sprint-1
  touch f3
  git add .
  git commit -m "c"
  touch f4
  git add .
  git commit -m "d"

3 Move back to master and create few more commits
  git checkout master
  touch f5
  git add .
  git commit -m "e"
  touch f6
  git add .
  git commit -m "f"

4 Merge sprint-1 with master
  git merge sprint1

5 Delete sprint-1 branch
  git branch -d sprint-1

6 Check commit history of master
  git log -oneline

git rebase: this is used for performing a fastforward merge
ie the commits coming from the branch are added to the top of the master branch.This is helpful when we want the commits coming from a branch to be reflected as the latest working version of code on master.

1 On the master create few commits
  touch f1
  git add .
  git commit -m "a"
  touch f2
  git add .
  git commit -m "b"

2 Create a new branch and create few commits on it
  git checkout -b sprint-1
  touch f3
  git add .
  git commit -m "c"
  touch f4
  git add .
  git commit -m "d"

3 Move back to master and create few more commits
  git checkout master
  touch f5
  git add .
  git commit -m "e"
  touch f6
  git add .
  git commit -m "f"

4 Rebase sprint-1 with master
  git checkout sprint-1
  git rebase master
  git checkout master
  git merge sprint-1


# Day 6

Rearranging the commit history
-------------------------------
The commit history can be changed according to
our requirment using the git rebase command
The latest commit or the top most commit is genrally
 called HEAD.We can make this HEAD point to any
older commit and make that older commit as the latest
commit

Note: The very first commit is called as initial
commit and this cannot be rearranged

git rebase -i HEAD~4

The number 4 represents the top 4 comits that we want
to rearrange
The above command will open the commit hsitory in vi
editor where can can simply change the commit order
Save and Quit   Esc :wq Enter


Git Squash
=============
Squash is merging of commits to make multiple 
commits to make it look like a single commit.

git rebase -i HEAD~4
The above command will open in vi editor
where the complete commit history is shown
Remove the pick word and replace it with
squash
Save and quit  esc : wq Enter  

Check the commit history
git log --oneline

Modifing exisiting commits
=============================
whenever we modify a file or create new files generally we create a new commit.Instead we can put the modifications in the existing commit itself rather than creating a new commit.
This can be done using git amend command

1 Create few commits in git LR
  touch f1
  git add .
  git commit -m "a"
  touch f2
  git add .
  git commit -m "b"
  touch f3
  git add .
  git commit -m "c"

2 Check the commit history
  git log --oneline

3 Modify some files or create new files
  cat > f3
  Put some data
  ctrl+d to comeout of cat

4 check status of git
  git status
  We will find a modified file

5 Send it to stagging area
  git add .

6 Commit it to local repositry as an exisiting commmit
  git commit --amend -m "c"

7 Check the commit history
  git log --oneline
  We will see that new commit is not created the changes are
  pushed into the exisiting "c" commit

Note: git amend actually creates a new commit.
The older "c" commit becomes an orphaned commit which 
cannot be see using git log

We can use "git reflog" for seeing the entire commit
history.ie active and orphaned commits


Git cherry pick
====================
This is used for choosing which commits we want to take
into the master branch
Generally when we perform "git merge" or "git rebase"
all the commits of that branch will come into master branch
Cherry pick will allow us to select only those commits that we require and merge them with master


1 Create few commits on master
  touch f1
  git add .
  git commit -m "a"
  touch f2
  git add .
  git commit -m "b"

2 Create a branch and some commits on it
  git checkout -b sprint-1

3 Create some commits here
  touch f3
  git add .
  git commit -m "c
  touch f4
  git add .
  git commit -m "d"
  touch f5
  git add .
  git commit -m "e"

4 Check the commit history on sprint-1 branch
  git log --oneline

5 Identify the commits that we want from sprint-1 branch
  and move back to master branch
  git checkout master
  git cherry-pick commit_id1 commit_id2

6 Check the commit history on master
  git log --oneline

git stash
==============
This is a feature of git which is used for leaving unfinished work and start a new functionality related coding.
Further command nof git should not touch the unfinished files

1 To stash the files present in stagging area
  git stash 

2 To stash the files present in stagging area and untracked  section
  git stash -u

3 To stash the files present in stagging area,untracked section   and also the .gitignore
  git stash -a

4 To see the list of all stashes that we have done
  git stash list

5 To unstash the latest stash
  git stash pop

6 To unstash any older stash
  git stash pop stash{stashno}
  Eg: To unstash the second last stash
      git stash pop stash{1}



172.31.34.177


# Day 7

1 Create a file and send to stagging area
  touch f1
  git add .

2 Stash the above file
  git stash

3 Create a new file and stash it
  touch f2
  git stash -u

4 Create few new files and place them in .gitignore
  Stash .gitignore also
  touch f3 f4 f5
  cat > .gitignore
  f3
  f4
  f5
  Press Ctrl+d to come out of cat command

5 Since f3,f4,f5 are put in .gitignore git status will no longer
  show them as untracked files but it will show .gitignore as   untracked file.ie further commands of git will send this   .gitignore into stagging area and also in local and remote   repositories.If we want ot avoid that and .gitignore should
  not be accessed by git
  git stash -a

Tagging in Git
==================
Tags are used for placing bookmarks on commits
They are to specify info related to who tagged ,when it was tagged and why it was tagged.
Generally used for releases
This helps in understanding what are the commits that are related to specific releases

Tags are of two types
1 Light weight tags
2 Annoted tags

1 To create a light weight tag
  git tag tabname

2 To see the list of all the tags 
  git tag

3 To create an annoted tag 
  git tag -a tagname -m "some message"

Note: Tags are always created for the latest commit(HEAD)

4 To create tags for an older commit
  git tag -a tagname -m "message" commit_id

5 To delete a localtag
  git tag -d tagname

6 To push all tags into github
  git push --tags

7 To delete tags from the remote github
  git push origin :tagname

  



git diff
------------
this is used for finding the difference between 2 commits
or it can be used for finding the difference between
a commit and a file yet to be commited


1 To find diff between 2 commits
  git diff commit1_id commit2_id

2 To find diff between latest commit and a file
  git diff HEAD filename


