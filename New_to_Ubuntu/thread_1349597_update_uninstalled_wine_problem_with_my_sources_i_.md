---
title: "update uninstalled wine? problem with my sources i think"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by jmcgovern on 2009-12-08
I've somehow managed to get wine uninstalled from my computer.  I think my sources.list got bungled up when i was trying to update it after I upgraded to Karmic.  When i attempt to install wine it says dependency missing.

heres the sources.list
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.cs.umn.edu/ubuntu/ karmic main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.cs.umn.edu/ubuntu/ karmic-updates main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.cs.umn.edu/ubuntu/ karmic universe
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic universe
deb http://mirror.cs.umn.edu/ubuntu/ karmic-updates universe
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.cs.umn.edu/ubuntu/ karmic multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic multiverse
deb http://mirror.cs.umn.edu/ubuntu/ karmic-updates multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.cs.umn.edu/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://mirror.cs.umn.edu/ubuntu/ karmic-security main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic-security main restricted
deb http://mirror.cs.umn.edu/ubuntu/ karmic-security universe
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic-security universe
deb http://mirror.cs.umn.edu/ubuntu/ karmic-security multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ karmic-security multiverse
deb http://mirror.cs.umn.edu/ubuntu/ karmic-proposed restricted main multiverse universe
deb http://packages.medibuntu.org/ karmic free non-free # disabled on upgrade to karmic
deb http://download.skype.com/linux/repos/debian/ stable non-free # disabled on upgrade to karmic
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main # disabled on upgrade to karmic
deb http://ubuntusatanic.org/hell karmic main # disabled on upgrade to karmic
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
```

---

### Post by mikewhatever on 2009-12-08
Nothing seems to be wrong with your sources, just install the missing dependency and then wine.

---

