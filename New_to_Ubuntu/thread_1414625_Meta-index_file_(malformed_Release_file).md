---
title: "Meta-index file (malformed Release file?)"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by medphys on 2010-02-23
Hi all,

Does anyone know what this means?

Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)

I get it when I try to update my system.  What is a malformed release file?

Thanks for your help.

---

### Post by gord-s on 2010-02-24
sounds like a typo error in /etc/apt/sources.list

please post output of

```
cat  /etc/apt/sources.list
``` from a terminal



"malformed Release file" usually means that something is wrong in the paths it's looking for, and that in turn is usually (though not always)  caused by a bad line or a typo in /etc/apt/sources.list.
The actual  Release  file itself is almost never "malformed", it's the files it's looking for that don't match up in the correct places, so the error is a little misleading sometimes

---

### Post by medphys on 2010-02-25
gord-s

Here is the output:

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main main'.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main'.
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse main'. universe
 


Hope this helps.

---

### Post by medphys on 2010-02-27
gord-s

Thanks for the help.  Corrected the names in sources.list fiel and everything works fine now.  

Thanks again

---

### Post by Alifar76 on 2010-11-29
I get the same error when I try to install Bio-Linux. 

W:Failed to fetch [http://nebc.nerc.ac.uk/bio-linux/dists/unstable/Release](http://nebc.nerc.ac.uk/bio-linux/dists/unstable/Release)  Unable to find expected entry  bio-linux/source/Sources in Meta-index file (malformed Release file?)

Following is my source.list. Please help. Thanks.


# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick main restricted
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-updates main restricted
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick universe
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick universe
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-updates universe
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick multiverse
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick multiverse
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-updates multiverse
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-security main restricted
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-security main
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-security universe
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-security universe
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-security multiverse
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) maverick-security multiverse
deb [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux
deb-src [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux

---

