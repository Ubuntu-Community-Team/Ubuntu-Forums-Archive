---
title: "Malformed Line in sources.list"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Light Knight 22 on 2011-01-18
When I try opening the Synaptic Package Manager or Software Center aswell as Reloading after visiting the Software Sources, I get an error. :

E: Malformed line 5 in source list /etc/apt/sources.list (URI parse) 
E: Unable to lock the list directory
Go to the repository dialogue to correct the problem. 
E: _cach->open() failed, please report. 


All I did was add *ppa:screenlets-dev/ppa *to the "other software" tab in Sotware Sources. Here is my sources.list. 
```

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb United States maverick main restricted
deb-src United States maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb United States maverick-updates main restricted
deb-src United States maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb United States maverick universe
deb United States maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb United States maverick multiverse
deb United States maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb United States maverick-security main restricted
deb-src United States maverick-security restricted main multiverse universe #Added by software-properties
deb United States maverick-security universe
deb United States maverick-security multiverse
# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) maverick cairo-dock ## Cairo-Dock-Stable disabled on upgrade to maverick
# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) maverick cairo-dock ## Cairo-Dock-Stable disabled on upgrade to maverick
# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main # disabled on upgrade to maverick
# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main # disabled on upgrade to maverick

# deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) maverick cairo-dock ## Cairo-Dock-Stable disabled on upgrade to maverick
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse #Added by software-properties
```

If I # line 5, then I have the same problem with line 6, then line 10... and so on. 

I really don't know what's wrong with my sources.list, nor how to add the screenlet's ppa safely.

---

### Post by slooksterpsv on 2011-01-18
Right number 5, 6, 10, 11, ... the ones that say deb United States is malformed, it has to be in the form of a url, such as:
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse

so:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse

is the correct way to add that one.

Do you have a backup of your sources.list?

---

### Post by kellemes on 2011-01-18
If needed you can regenerate one here..
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by Light Knight 22 on 2011-01-18
I replaced all the malformed lines with deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse.

It works now. 

I don't have a backup of sources.list. I probably should eh?

Thanks!

---

