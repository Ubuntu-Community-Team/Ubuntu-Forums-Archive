---
title: "sudo apt get nonfunctional in 8.10 on acer aspire one"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by jdshelby on 2009-03-23
Hi All, 
I just installed 8.10 onto my acer aspire one netbook from a burned CD.  For some reason, the sudo apt-get command isn't working for anything.  I went into synaptic, and all the repositories are checked.  Tried it again, and nothing.

Any tips?
J.

---

### Post by iaculallad on 2009-03-23
Does it display any error? Post the complete command you're trying to execute.

---

### Post by jdshelby on 2009-03-23
Here's what it gives me (I'm actually now working in Xubuntu -- but same problem: 

justin@justin-laptop:~$ sudo apt-get install xubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xubuntu-restricted-extras

---

### Post by iaculallad on 2009-03-23
Try to post your sources.list file content by issuing the command below on your terminal:

```
cat /etc/apt/sources.list
```

---

### Post by jdshelby on 2009-03-23
Here we go:

justin@justin-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030.3)]/ intrepid main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
justin@justin-laptop:~$

---

### Post by kevmitch on 2009-03-23
Have you done an
```
apt-get update
```
?

---

### Post by jdshelby on 2009-03-23
Wow -- that'll do it.  If you don't mind, could you tell me what the problem was?  I'd installed Ubuntu several times and never run into this problem.  What was going on?

Thanks
Justin

---

### Post by kevmitch on 2009-03-23
You had all the repositories listed in sources.list, but you had no local package database containing their contents. You were thus querying an empty database. I'm not exactly sure why this wouldn't have been a problem before. It's likely that synaptic or the update manager or something usually does the update invisibly. Maybe you were just quicker to install stuff from the command this time ;).

---

