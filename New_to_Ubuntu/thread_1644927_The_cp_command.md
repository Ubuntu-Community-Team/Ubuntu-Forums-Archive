---
title: "The cp command"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by yc2 on 2010-12-13
Hello,

When I use the copy command, often with wildcards, I am sometimes not sure of the outcome. Maybe I have been misguided through assuming that I am running DOS ;)

For example this does not work of course
```
WRONG:
cp *.htm    dir2/*.html
```
It should be
```
cp *.htm dir2
```
and then use the rename command

I do not know how to merge one directory into another (replace files that have the same name).
```
cp dir1 another_location/dir1
```
will not do the trick (it will create another_location/dir1/dir1 (if the destination directory exists), I think)
(The merging option is the default in f.ex. Windows click and drag copying.)

I think the comparison with Windows is relevant since many Linux users have started out with Windows and some of them assume everything is the same.

I am trying to write an introduction to Ubuntu in Swedish and want to shed some light on this. Can anyone please help me on this subject. F.ex. how to merge directories and also somehow describe the most significant differences between dos/copy and shell/cp

I am not sure this is the right board, but the question relates to bash so I hope it is OK.

Thanks.


EDIT:
Here's another difference:
I think you must use
cp -R
to get all subdirectories?
And also the hidden files do not enter the cp command in some systems?

---

### Post by trent.josephsen on 2010-12-13
You seem to have two questions, one about shell wildcard expansion and one about cp.

cp -r is recursive; I think -R does the same thing.  man cp will get you more info.

* will not match dotfiles (in most shells), but that has nothing to do with cp.

---

### Post by yc2 on 2010-12-13
Yes, the questsion is like:
_What bad surprises can a user have if he hasn't read man cp carefully, but just makes some erroneous assumptions?_ Every new user does not read man cp before start using the system.

Another one is, I think, that all systems do not include hidden (.name) files if you just use cp.

---

### Post by trent.josephsen on 2010-12-14
> **trent.josephsen said:**
> *** will not match dotfiles (in most shells), but that has nothing to do with cp.**

cp -r dir newDir will indeed copy dotfiles within dir.

cp dir/* newDir/ will not match dotfiles within dir, any more than rm ~/* will match dotfiles within your home directory.

---

### Post by CharlesA on 2010-12-14
This has nothing to do with Programming. Moved to ABT.

---

### Post by QLee on 2010-12-14
[QUOTE=yc2]...
I think the comparison with Windows is relevant since many Linux users have started out with Windows and some of them assume everything is the same.
...[/QUOTE]

May I respectfully disagree with you about this? I don't think Ubuntu, or GNU/Linux in general should be particularly concerned with user's mistaken assumptions. And, there isn't really a way for a derivative Distro to affect what comes down from upstream, except by education and there are lots of, new user, and, users who are switching, guides available. The responsibility for learning has to fall on the individual.

Have a look at this document:
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Philosophy](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Philosophy)

---

