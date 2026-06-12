---
title: "Segmentation faultsts error"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2009-09-02
I got an upgrade notification today and when I went into terminal like I normaly do I got back this. When I run apt-get update, it runs through available updates and checks repositories like normal and then it tells me segmentation faultsts. I tried using the update manager but every time I click it from the task bar it pops up and crashes right away. I went into synaptic and it loads and allows me to search, but if I try to install or remove any applictions to also crashes.  This all started after I added a ppa repo for vlc because I was looking for the newest VLC. I didn't like the one included in the main Ubuntu repositories because it has 2 different windows for control and video, I wanted them both together. Any ideas?

```
gary@gary-laptop:~$ sudo apt-get upgrade
Segmentation faultsts... 0%
gary@gary-laptop:~$ 
```

I also include my sources list just in case you all think it might be part of the problem. 
```
gary@gary-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
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
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock
**deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main**
gary@gary-laptop:~$ 

```

---

### Post by Bigtime_Scrub on 2009-09-08
I managed to fix this by rebooting, unchecking the ppa for VLC, uninstalling, and then reinstalling VLC from the Ubuntu repository. I guess for some reason it doesn't play nice with my system. Anyway it is fixed now but with the earlier version on VLC and not the newest one. I erased the ppa repository. Still though if someone knows what a faultsts error is I would like to know because I've never seen it before.

---

