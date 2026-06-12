---
title: "error"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Mysantiaguin on 2011-02-05
Hello, I have this problem when I try to start the Update Manager:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'

Could somebody help me?

Thanks,

---

### Post by DiSTORT3D on 2011-02-05
can you post output? ```
cat /etc/apt/sources.list
```

---

### Post by 3rdalbum on 2011-02-05
> **Mysantiaguin said:**
> Hello, I have this problem when I try to start the Update Manager:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'

Could somebody help me?

Thanks,

When you edited the /etc/apt/sources.list file, you made a mistake on or around line 59. Open that file again and reverse whatever you did to it, then run 'sudo apt-get update'.

In future, use the Repositories editor in Synaptic or Software Center to add a new repository, it makes it impossible for this problem to occur.

---

### Post by Mysantiaguin on 2011-02-08
> **3rdalbum said:**
> When you edited the /etc/apt/sources.list file, you made a mistake on or around line 59. Open that file again and reverse whatever you did to it, then run 'sudo apt-get update'.

In future, use the Repositories editor in Synaptic or Software Center to add a new repository, it makes it impossible for this problem to occur.


Thanks 4 your help. Could you tell how can I open that file and reverse what I did? I was trying to install Java and something was wrong in the middle, after that I got this problem.

Thanks.

---

### Post by Linyx on 2011-02-08
> **Mysantiaguin said:**
> Thanks 4 your help. Could you tell how can I  open that file and reverse what I did? I was trying to install Java and  something was wrong in the middle, after that I got this problem.

Thanks.

Post the output of the Code which was mentioned by [DiSTORT3D]("http://ubuntuforums.org/member.php?u=1237395").

You can open it with a default GUI Text-Editor Gedit, Type the command in terminal

```
gedit /etc/apt/sources.list
```

Moreover, if the installation is stopped in the middle, it will be better to run the command:-
```
sudo dpkg --configure -a
```

---

### Post by gordintoronto on 2011-02-08
Make that:
gksudo gedit /etc/apt/sources.list

---

### Post by Mysantiaguin on 2011-02-09
> **DiSTORT3D said:**
> can you post output? ```
cat /etc/apt/sources.list
```

Hope you can do something with it.
Thanxs.

santiago@Santiago:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

---

### Post by smurphy_it on 2011-02-09
your last two lines don't look right, looks like the space was removed.  Also, if you aren't running lucid, you should have that pointing to the right distro.

Original Lines:
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner  (note, no space after/ and before lucid)
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner 

Change Lines to:

deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner 

afterwords, you can open a terminal and type sudo apt-get update

---

### Post by Mysantiaguin on 2011-02-10
> **smurphy_it said:**
> your last two lines don't look right, looks like the space was removed.  Also, if you aren't running lucid, you should have that pointing to the right distro.

Original Lines:
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner  (note, no space after/ and before lucid)
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner 

Change Lines to:

deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner 

afterwords, you can open a terminal and type sudo apt-get update


Thanks for your help! I`m new in Ubuntu and I don`t have idea how can I do to change the lines...
Could you explain me this?
Thanks!

---

### Post by Linyx on 2011-02-11
> **Mysantiaguin said:**
> Thanks for your help! I`m new in Ubuntu and I don`t have idea how can I do to change the lines...
Could you explain me this?
Thanks!

Open the file as a root, type in terminal:-

```
gksudo gedit /etc/apt/sources.list
```

Once it is open, then you can edit it....Now Follow the above post...

---

### Post by Mysantiaguin on 2011-02-11
> **Linyx said:**
> Open the file as a root, type in terminal:-

```
gksudo gedit /etc/apt/sources.list
```Once it is open, then you can edit it....Now Follow the above post...


It worked!! I could do the update!

Thanks!

---

### Post by Mysantiaguin on 2011-02-11
> **smurphy_it said:**
> your last two lines don't look right, looks like the space was removed.  Also, if you aren't running lucid, you should have that pointing to the right distro.

Original Lines:
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner  (note, no space after/ and before lucid)
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner 

Change Lines to:

deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner 

afterwords, you can open a terminal and type sudo apt-get update


It worked fine! Thanks a lot!

---

### Post by Linyx on 2011-02-11
Welcome....Now you can mark **thread-as-solved** in **Thread-Tools** above...

---

