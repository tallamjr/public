# Public and Private Repo's

How to have an open public repository as well as a mirrored private repository on Github

These steps were inspired from this guide of '[Mirroring a
repository'](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/duplicating-a-repository#mirroring-a-repository) on Github documentation

1.
```bash
14:05:04 ✔ ~/Github/origin  :: git clone --bare git@github.com:tallamjr/public.git private
Cloning into bare repository 'private'...
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (5/5), 5.47 KiB | 5.47 MiB/s, done.
14:05:45 ✔ ~/Github/origin  :: cd private/
```

2.

```bash
14:05:48 ✔ ~/Github/origin/private (BARE:master) :: git push --mirror git@github.com:tallamjr/private.git
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 5.47 KiB | 5.47 MiB/s, done.
Total 5 (delta 0), reused 5 (delta 0)
To github.com:tallamjr/private.git
 * [new branch]      master -> master
14:06:13 ✔ ~/Github/origin/private (BARE:master) :: cd ../
```

3.

```bash
14:06:24 ✔ ~/Github/origin  :: rm -rf private/
```

4.

```bash
14:06:30 ✔ ~/Github/origin  :: git clone git@github.com:tallamjr/private.git
Cloning into 'private'...
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (4/4), done.
Receiving objects: 100% (5/5), 5.47 KiB | 5.47 MiB/s, done.
remote: Total 5 (delta 0), reused 5 (delta 0), pack-reused 0
14:07:04 ✔ ~/Github/origin  :: cd private/
14:07:06 ✔ ~/Github/origin/private (master) :: git remote -v
origin  git@github.com:tallamjr/private.git (fetch)
origin  git@github.com:tallamjr/private.git (push)
```

5.

```bash
14:08:04 ✘ ~/Github/origin/private (master) :: git remote add upstream git@github.com:tallamjr/public.git
14:09:22 ✔ ~/Github/origin/private (master) :: git remote -v
origin  git@github.com:tallamjr/private.git (fetch)
origin  git@github.com:tallamjr/private.git (push)
upstream        git@github.com:tallamjr/public.git (fetch)
upstream        git@github.com:tallamjr/public.git (push)
```

6.

```bash
14:10:25 ✔ ~/Github/origin/private (master) :: cd ../
14:10:41 ✔ ~/Github/origin  :: git clone git@github.com:tallamjr/public.git
Cloning into 'public'...
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (5/5), 5.47 KiB | 5.47 MiB/s, done.
14:10:50 ✔ ~/Github/origin  :: cd public/
14:10:52 ✔ ~/Github/origin/public (master) :: vim README.md
14:18:15 ✔ ~/Github/origin/public (master) :: git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

7.

```bash
14:19:13 ✔ ~/Github/origin/public (master) :: git add README.md
14:19:42 ✔ ~/Github/origin/public (master) :: git commit
[master 881d666] Updating README with instructions
 1 file changed, 82 insertions(+), 1 deletion(-)
 rewrite README.md (100%)
14:20:36 ✔ ~/Github/origin/public (master) :: git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
14:20:37 ✔ ~/Github/origin/public (master) :: git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 1.04 KiB | 1.04 MiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:tallamjr/public.git
   ba0bb9d..881d666  master -> master
```
