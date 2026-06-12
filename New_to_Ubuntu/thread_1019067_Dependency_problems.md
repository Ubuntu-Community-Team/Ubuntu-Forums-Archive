---
title: "Dependency problems"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by seuzy13 on 2008-12-22
Trying to install cinelerra on Intrepid:

"
cinelerra:
 Depends: liblame0 but it is not going to be installed
 Depends: libopenexr2c2a (>=1.2.2) but it is not installable
 Depends: libquicktimehv but it is not going to be installed
 Depends: libquicktimehv but it is not going to be installed
"

Basically, I've had this problem when trying to install many different programs, but when I go to install the first dependency (liblame0), the package manager wants to remove a host of other useful packages like avidemux, ogmrip, mencoder, and libmp3lame0.

How do I get these packages to coexist peacefully?

---

### Post by taurus on 2008-12-22
Did you download cinelerra and install it by hand?

---

### Post by abn91c on 2008-12-22
> **seuzy13 said:**
> Trying to install cinelerra on Intrepid:

"
cinelerra:
 Depends: liblame0 but it is not going to be installed
 Depends: libopenexr2c2a (>=1.2.2) but it is not installable
 Depends: libquicktimehv but it is not going to be installed
 Depends: libquicktimehv but it is not going to be installed
"

Basically, I've had this problem when trying to install many different programs, but when I go to install the first dependency (liblame0), the package manager wants to remove a host of other useful packages like avidemux, ogmrip, mencoder, and libmp3lame0.

How do I get these packages to coexist peacefully?
in a terminal sudo dpkg --configure -a
then sudo apt-get install -f

---

### Post by seuzy13 on 2008-12-22
> **taurus said:**
> Did you download cinelerra and install it by hand?

I added the repositories for it. The real problem though seems to lie with one of its dependencies, liblame0.

abn91c, those commands did not work for me. :(

I might add that mplayer is listed under the programs that need to be autoremoved. Something's amiss here.

---

### Post by taurus on 2008-12-22
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by seuzy13 on 2008-12-22
> 
Can you post your /etc/apt/sources.list?


I'm afraid it's quite a mess.

```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/
# deb http://ppa.launchpad.net/fta/ubuntu hardy main
# deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
# deb http://ubuntu.p2p-next.org/ hardy main

#ULTAMATIX REPOS START


deb-src http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb-src http://us.archive.ubuntu.com/ubuntu hardy multiverse

deb http://us.archive.ubuntu.com/ubuntu hardy multiverse

deb http://repoubuntusoftware.info harty all

deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://security.ubuntu.com/ubuntu hardy-security multiverse

deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://security.ubuntu.com/ubuntu hardy-security universe

deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb http://security.ubuntu.com/ubuntu hardy-security main restricted

deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.canonical.com/ubuntu hardy partner

# deb http://repoubuntusoftware.info harty all

# deb http://repoubuntusoftware.info harty all

deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.canonical.com/ubuntu intrepid partner
#ULTAMATIX REPOS END
# deb http://www.bashterritory.com/pytube/releases/ /
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu intrepid/
# deb http://packages.medibuntu.org/ intrepid free non-free #Medibuntu
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
# PulseAudio Fixes & Adobe Flash - Preview Packages (psyke83)
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb http://ppa.launchpad.net/arnegoetje/ubuntu intrepid main
deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb http://ppa.launchpad.net/do-core/ubuntu intrepid main
deb-src http://ppa.launchpad.net/do-core/ubuntu intrepid main
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
# deb ftp://ftp.debian.org/debian experimental main
deb http://apt.boxee.tv intrepid main

```

---

### Post by taurus on 2008-12-22
Obviously, you are running intrepid but somehow you have repo for hardy in there. 

```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/
```

Then, you have ultamatrix!

---

### Post by seuzy13 on 2008-12-22
> **taurus said:**
> Obviously, you are running intrepid but somehow you have repo for hardy in there. 

```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/
```

Then, you have ultamatrix!

Okay, so what should I do about this? I think when I did my distribution upgrade a month or so ago, some things didn't carry over well. Miro doesn't update anymore (along with about eleven other packages) and the hardy repo might explain that.

---

### Post by seuzy13 on 2008-12-22
I removed the ultamatix and old miro repos and that worked.

Thanks! :)

---

