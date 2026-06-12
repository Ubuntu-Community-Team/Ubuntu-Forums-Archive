---
title: "Ubuntu's source list"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by cam3roon on 2010-10-13
Hi. I'm new to Ubuntu. My first one is 10.10 so imagine the experience that I have with it. Anyway, the problem is that after visiting many websites, I changed the sources.list a number of times, so now I started to have weird errors when I'm trying to update. Can you please give me a source list that is good and complete? Or, where can I get one?

Sorry about the possibly stupid question that I made, but screwing it up is a way to learn :D

Thanks

---

### Post by howefield on 2010-10-13
Here is what is in mine. A default install so far untouched.

```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse


```

---

### Post by cam3roon on 2010-10-13
Thank you a lot! Most of the errors are gone, but I still have this one.

[IMG]http://img823.imageshack.us/img823/1738/screenshotlag.png[/IMG]

---

### Post by howefield on 2010-10-13
Load up System > Administration > Synaptic Package Manager and go into Settings > Repositories > Other Software tab, then deselect the troublesome lines or do it by editing your sources.list using this command

> gksudo gedit /etc/apt/sources.list

and place a # sign in front of the troublesome lines.

It is probably easier and safer to so it the first way.

---

### Post by plucky on 2010-10-13
Open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get update
``` and post the output to the forum.Your screenshot doesn't show the whole error message.

You seem to have some PPA's added to your sources.list which are causing problems.

For a new sources.list go [Here](http://repogen.simplylinux.ch/)

Good Luck

---

### Post by cam3roon on 2010-10-13
It worked the first way. Thank you very much.

---

### Post by howefield on 2010-10-13
> **cam3roon said:**
> It worked the first way. Thank you very much.

You are welcome. Do call again. :)

---

