---
title: "Upgrade UNR 8.04"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2009-05-01
I need help upgrading Ubuntu Netbook Remix 8.04 to 9.04 (Which I believe must go though 8.10). How may I go about doing this because standard upgrade methods are not working.

---

### Post by pi.boy.travis on 2009-05-01
Correct me if I'm wrong, but you will need to do a fresh install of 9.04.  "Skipping" versions is not supported.  I would recommend backing up your data and doing a clean install.

---

### Post by linuxguymarshall on 2009-05-01
So I can not upgrade to 8.10 then to 9.04? My flash drive has been filled to capacity and I really don't want to burn another DVD

---

### Post by pi.boy.travis on 2009-05-01
8.10 didn't have a netbook remix in the same sense that 8.04 and 9.04 have.

We can try to do it manually, can you post your /etc/apt/sources.list?

---

### Post by linuxguymarshall on 2009-05-01
Read it and weep. All of the sources seem to be 'netbook remix' sources.

```
deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse universe
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
```

---

### Post by linuxguymarshall on 2009-05-02
Do I really have to reformat?

---

### Post by pi.boy.travis on 2009-05-02
You can try using my UNR 9.04 sources.list:

```
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```


That might do the trick.  Just be careful to save your old sources.list just in case. . .

---

### Post by blackened on 2009-05-02
You should be prepared to do a clean install even if you try the upgrade. Skipping releases like that, it is a very good possibility that the upgrade will go horribly awry and will break your current installation forcing you to clean install anyway.

Granted, everything may go great and you may loose nothing. That whole "Be Prepared" thing is some good advice, despite who it's attributed to.

---

