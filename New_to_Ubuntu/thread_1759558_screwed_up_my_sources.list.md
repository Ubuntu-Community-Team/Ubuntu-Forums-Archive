---
title: "screwed up my sources.list"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by Missi0n on 2011-05-15
im an idiot, how to i fix it?


```
# deb cdrom:[Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://packages.medibuntu.org/ natty free non-free
deb-src http://packages.medibuntu.org/ natty free non-free
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
```

---

### Post by 5149.5 on 2011-05-15
Your last two lines say: lucid partner at the end. Change the lucid to natty and try it again.

---

### Post by PunkLV on 2011-05-15
Use this in the future.
sources.list generator for Debian as well as Ubuntu: [http://debgen.simplylinux.ch/](http://debgen.simplylinux.ch/)

---

### Post by Missi0n on 2011-05-16
> **5149.5 said:**
> Your last two lines say: lucid partner at the end. Change the lucid to natty and try it again.

This did not work

---

### Post by SaneWarning on 2011-05-16
The problem appears to be with:
```
deb http://archive.canonical.com/lucid partner
``````
deb-src http://archive.canonical.com/lucid partner
```Which should be:
```
deb http://archive.canonical.com/ubuntu natty partner
``````
deb-src http://archive.canonical.com/ubuntu natty partner
```But this appears to already be in your sources.list file.

---

### Post by 5149.5 on 2011-05-16
> **Missi0n said:**
> This did not work

Hmmmm. Those two lines are 61 and 62. Line 61 is triggering the error msg according to your screenshot. They are also the only lines for the lucid release and the rest are natty. You are running natty, right?

---

### Post by dcsoldschool53 on 2011-05-16
First, close source.list, and do a backup of your source list file. I do not know anything about Xubuntu```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
```If you made the change like everyone said, goto the terminal to do```
sudo apt-get update
```If it still does not work, try putting a double # pound sign (no space between ##) in front of those two entries. Then, in a terminal, do```
sudo apt-get update
```Hope this helps and good luck!

---

