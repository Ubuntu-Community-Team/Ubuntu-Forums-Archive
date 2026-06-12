---
title: "[SOLVED] Installing WinFF"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-12-19
Ok, I'm trying to install WinFF.  I downloaded it onto my desktop as a tar.gz but there's no instructions inside of what I need to do to get it working.

---

### Post by kostkon on 2008-12-19
For installation in Ubuntu, check [the instructions here]("http://code.google.com/p/winff/wiki/UbuntuInstallation").

---

### Post by Nazty_Nayt on 2008-12-19
Ok I tried that, I used the synaptic rout and after the last step it says push reload, after I press reload I get this error

> Failed to fetch [http://archive.ubuntu.com/dists/YOURDIST/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/YOURDIST/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/dists/YOURDIST/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/YOURDIST/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by stanz on 2008-12-19
Me thinks ya need to replace the "/YOURDIST/" with what cha got in your box..
Hardy, or Intrepid, etc...

---

### Post by albinootje on 2008-12-19
> **Nazty_Nayt said:**
> Ok I tried that, I used the synaptic rout and after the last step it says push reload, after I press reload I get this error

Running Ubuntu Feisty ? Feisty is officially no longer supported.
Check the ubuntuforums for the unofficial repositories for it.

---

### Post by kostkon on 2008-12-19
Could you post the contents of your sources.list file. Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and do
```
gedit /etc/apt/sources.list
```
and post the contents of the file here.

---

### Post by Nazty_Nayt on 2008-12-19
I kinda figured I had to changed the your dist part, I'm running Hardy.  The thing was I didn't know where it was entered as I just followed the commands from the link.  After koston asked me for the sources list which are below I guess I change it there, right?

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock

deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main

deb http://archive.ubuntu.com YOURDIST main universe
```

---

### Post by kostkon on 2008-12-19
> **Nazty_Nayt said:**
> I kinda figured I had to changed the your dist part, I'm running Hardy.  The thing was I didn't know where it was entered as I just followed the commands from the link.  After koston asked me for the sources list which are below I guess I change it there, right?

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock

deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main

deb http://archive.ubuntu.com YOURDIST main universe
```
OK. Open the *sources.list* file again, this time with admin priviledges, i.e.
```
gksudo gedit /etc/apt/sources.list
```
delete the last line, save the file, and in the terminal, again, do
```
sudo apt-get update
```
it should produce no errors.
Afterwards, try to follow the instructions again on the winff page. If you have any problem following them then ask here for help.

---

### Post by Nazty_Nayt on 2008-12-19
Thanks Kostcon, got it up and running.  Appreciate all the help.

---

