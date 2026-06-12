---
title: "Problem with downloads"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by itsvan on 2010-08-31
Hi i was trying to install the missing plugins necessary to watch you tube videos,,normally it does this fine,,but now its acting up,,neither do any of the normal downloads from the ubuntu software center work..what can i do?

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


im on ubuntu 10.04

---

### Post by wojox on 2010-08-31
It's looking for 10.1.53.64ubuntu0.10.04.3_i386.deb but it's not there [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

---

### Post by itsvan on 2010-08-31
yah but it seems its doing that for all the files it wants to download..how can i fix this...also apparently my xserver is having problems,,,because everytime i reboot it loogs me in to text menu..and i have to enter sudo dpkg-reconfigure-xserver-xorg to get it back running to normal

---

### Post by 3rdalbum on 2010-08-31
Update your package list:

```
sudo apt-get update
```

If you still get the 404 Not Found error, then try changing your mirror in System > Administration > Software Sources.

---

### Post by varunendra on 2010-09-01
Hmm.. bad avatar itsvan, unapproved at my place! My boss thought I'm on a *bad* site.. !! :lolflag:

Onto your problem:
I'm not sure if it may help, but have you checked your **/etc/apt/sources.list** file that it contains the line:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse?
It should be there & there should be no # sign before it.

My experimental installation's (in VMware) sources.list file doesn't have many sources added, yet it is able to retrieve all those packages from all the repositories. You may wish to look at it for comparison:
```
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid universe main multiverse restricted #Added by software-properties
deb http://archive.canonical.com/ lucid partner
deb http://www.geekconnection.org/remastersys/repository karmic/
deb http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main
```

---

