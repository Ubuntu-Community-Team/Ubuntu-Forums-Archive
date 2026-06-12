---
title: "Amarok 2.0"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by cerealtx on 2008-12-25
i had the old amarok and im trying ot install 2.0, i added the repository
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```
then went through synaptic and tried to install amarok-kde4 but it gives me a whole list of problems
```
amarok-kde4:
 Depends: kdebase-runtime but it is not going to be installed
 Depends: kdelibs5 but it is not going to be installed
  Depends: libc6 (>=2.8~20080505) but 2.7-10ubuntu4 is to be installed
  Depends: libgcrypt11 (>=1.4.0) but 1.2.4-2ubuntu7 is to be installed
 Depends: libmtp8  but it is not installable
 Depends: libphonon4 but it is not going to be installed
 Depends: libqt4-dbus but it is not going to be installed
 Depends: libqt4-network but it is not going to be installed
 Depends: libqt4-opengl but it is not going to be installed
 Depends: libqt4-script but it is not going to be installed
 Depends: libqt4-sql but it is not going to be installed
 Depends: libqt4-svg but it is not going to be installed
 Depends: libqt4-webkit but it is not going to be installed
 Depends: libqt4-xml but it is not going to be installed
 Depends: libqtcore4 but it is not going to be installed
 Depends: libqtgui4 but it is not going to be installed
 Depends: libstreamanalyzer0 but it is not going to be installed
 Depends: libstreams0 but it is not going to be installed
  Depends: libtag1c2a (>=1.5) but 1.4-8ubuntu1 is to be installed
 Depends: phonon (>4:4.2.0) but it is not installable
```
any ideas? im runnign Gnome as my window manager, but amarok the old one worked with it, so do i have to use KDE4 ? is that the problem?

---

### Post by igknighted on 2008-12-25
Are you using Hardy?

EDIT: Can you post your /etc/apt/sources.list file?  You might be missing a repo

---

### Post by cerealtx on 2008-12-25
I am using hardy
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```

---

### Post by igknighted on 2008-12-25
That repo is for intrepid.  Change the word intrepid in your sources.list file to hardy and reload the repo's and you should be alright.  I checked the PPA quick and I think there is a hardy version in there.

---

### Post by pyromanic123boom on 2008-12-25
Yeah, you have to add another repository, I believe. 
However, when I installed it ( a few weeks ago, I forget how I did), there were sound problems and I couldn't get anything to play. I recommend against using it right now as it isn't working well with Ubuntu.

---

### Post by cerealtx on 2008-12-25
thank you very much!!

---

