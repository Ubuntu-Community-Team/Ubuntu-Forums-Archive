---
title: "Error using a local repository, HELP"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-06-28
I am getting this error, when i try to use my LOCAL repository I mirroed using apt-mirror, E: The method driver /usr/lib/apt/methods/ffile could not be found.
E: The method driver /usr/lib/apt/methods/ffile could not be found.


```
#deb cdrom:[Ubunts of the distribution.

deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid universe
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb file:/home/eric/mirror/archive.canonical.com/ubuntu lucid partner
deb-src file:/home/eric/mirror/archive.canonical.com/ubuntu lucid partner

deb file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security main restricted
deb-src file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security main restricted
deb file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security universe
deb-src file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security universe
deb file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security multiverse
deb-src file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security multiverse
deb file:/home/eric/mirror/mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
deb-src file:/home/eric/mirror/mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
deb file:/home/eric/mirror/mirror.oscc.org.my/medibuntu/ lucid free non-free
deb-src file:/home/eric/mirror/mirror.oscc.org.my/medibuntu/ lucid free non-free
deb ffile:/home/eric/mirror/ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-free
deb-src file:/home/eric/mirror/ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-freeu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid universe
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src file:/home/eric/mirror/us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb file:/home/eric/mirror/archive.canonical.com/ubuntu lucid partner
deb-src file:/home/eric/mirror/archive.canonical.com/ubuntu lucid partner

deb file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security main restricted
deb-src file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security main restricted
deb file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security universe
deb-src file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security universe
deb file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security multiverse
deb-src file:/home/eric/mirror/security.ubuntu.com/ubuntu lucid-security multiverse
deb file:/home/eric/mirror/mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
deb-src file:/home/eric/mirror/mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
deb file:/home/eric/mirror/mirror.oscc.org.my/medibuntu/ lucid free non-free
deb-src file:/home/eric/mirror/mirror.oscc.org.my/medibuntu/ lucid free non-free
deb file:/home/eric/mirror/ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-free
deb-src file:/home/eric/mirror/ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-free
```

---

### Post by diesch on 2010-06-28
In
```
deb ffile:/home/eric/mirror/ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-free
```
replace *ffile* with *file*

---

