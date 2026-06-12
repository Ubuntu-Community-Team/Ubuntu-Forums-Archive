---
title: "Problems installing ffmpeg"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-11-19
Trying to install ffmpeg in Karmic but keep getting this :-

office@office-laptop:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ffmpeg: Depends: libavcodec52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavdevice52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavfilter0 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavformat52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavutil50 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libpostproc51 (>= 5:0.5+svn20091116) but 4:0.5+svn20090706-2ubuntu2 is to be installed
          Depends: libswscale0 (>= 5:0.5+svn20091116) but it is not going to be installed
E: Broken packages


Any ideas ????

---

### Post by mc4man on 2009-11-19
> Any ideas ????

Pretty simple, ck. your sources, those versions are certainly not from any ubuntu repo.
Do you have any ppa's enabled or debian-multimedia? ( looks like the dm naming, though it's up to svn20091118 atm

---

### Post by celticbhoy on 2009-11-19
Got a few - any idea what ones causing the problem :-

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha i386 (20090905)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse

deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main

deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

---

### Post by mc4man on 2009-11-19
Can't really say, ubuntu-tweak can mess up your install in countless ways.

Maybe open synaptic, search ffmpeg and under it's properties look for the version, may give you a clue as to what source is/was providing it

Also look in System -> Admin -> Software Sources -> third party and see what's there (enabled or not, maybe at this point just enable or disable them all (your choice there) and run

 sudo apt-get update

Between ubuntu-tweak and karmic-proposed if you've been doing blanket updates thru the update manager  then you may have all sorts of 'non-standard' packages installed

---

