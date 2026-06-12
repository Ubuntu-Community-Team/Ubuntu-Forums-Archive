---
title: "Can not install libglu1-mesa-dev or libqt4-dev"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-09-12
I want to install a program called Stellarium. I am running Ubuntu 9.04 64 bit, so I have to compile from source. I tried to follow the instructions and make sure I had all of the dependencies from [http://stellarium.org/wiki/index.php/Build_Dependencies](http://stellarium.org/wiki/index.php/Build_Dependencies). But when I try and install libglu1-mesa-dev and libqt4-dev I get errors. I am attaching screen shots of the two errors I get. 

Any idea how to get them installed?

---

### Post by perce on 2009-09-12
Stellarium is in the repository: 
```
sudo apt-get install stellarium
```
no need of compiling it.

---

### Post by slughappy1 on 2009-09-12
Ok, thanks. Can you tell me why they won't install though?

So if I wanted to try svn versions when they change

---

### Post by mc4man on 2009-09-12
> Ok, thanks. Can you tell me why they won't install though?

I'm gathering that you're running jaunty with one or more  karmic sources enabled

---

### Post by slughappy1 on 2009-09-13
...no. At least not that I'm aware of. My /etc/apt/sources.list looks like
```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.xmission.com/ubuntu/ jaunty main restricted
deb-src http://mirrors.xmission.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.xmission.com/ubuntu/ jaunty-updates main restricted
deb-src http://mirrors.xmission.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.xmission.com/ubuntu/ jaunty universe
deb-src http://mirrors.xmission.com/ubuntu/ jaunty universe
deb http://mirrors.xmission.com/ubuntu/ jaunty-updates universe
deb-src http://mirrors.xmission.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.xmission.com/ubuntu/ jaunty multiverse
deb-src http://mirrors.xmission.com/ubuntu/ jaunty multiverse
deb http://mirrors.xmission.com/ubuntu/ jaunty-updates multiverse
deb-src http://mirrors.xmission.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirrors.xmission.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://mirrors.xmission.com/ubuntu/ jaunty-security main restricted
deb-src http://mirrors.xmission.com/ubuntu/ jaunty-security main restricted
deb http://mirrors.xmission.com/ubuntu/ jaunty-security universe
deb-src http://mirrors.xmission.com/ubuntu/ jaunty-security universe
deb http://mirrors.xmission.com/ubuntu/ jaunty-security multiverse
deb-src http://mirrors.xmission.com/ubuntu/ jaunty-security multiverse

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Banshee - https://edge.launchpad.net/~banshee-team
## Run this command: gpg --keyserver subkeys.pgp.net --recv 6E80C6B7 && gpg --export --armor 6E80C6B7  | sudo apt-key add -
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main

#### Blueman - https://edge.launchpad.net/~blueman/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
deb http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main 

#### Chromium Project - http://code.google.com/chromium/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add -
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

#### Conky - https://launchpad.net/conky
## Run this command: gpg --keyserver subkeys.pgp.net --recv 95628707 && gpg --export --armor 95628707 | sudo apt-key add -
deb http://ppa.launchpad.net/norsetto/ppa/ubuntu jaunty main

#### Gnome-Do - http://do.davebsd.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 77558DD0 && gpg --export --armor 77558DD0  | sudo apt-key add -
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/index.html
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free

#### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ jaunty free non-free 

#### Miro HD Video Player - http://www.getmiro.com/
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu jaunty/ 

#### OpenOffice.org 3.0 - https://launchpad.net/~openoffice-pkgs/+archive
## Run this command: gpg --keyserver subkeys.pgp.net --recv 247D1CFF && gpg --export --armor 247D1CFF  | sudo apt-key add -
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main

#### Playdeb - http://www.playdeb.net/
## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu jaunty-getdeb games

#### PlayOnLinux - http://www.playonlinux.com
## Run this command: sudo apt-get update && sudo apt-get install playonlinux
deb http://deb.playonlinux.com/ jaunty main

#### Wine - http://www.winehq.org/
## Run this command: wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
deb http://wine.budgetdedicated.com/apt jaunty main

#### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: gpg --keyserver subkeys.pgp.net --recv AF1CDFA9 && gpg --export --armor AF1CDFA9  | sudo apt-key add -
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main


####### 3rd Party Source Repos

#### Banshee (Source) - https://edge.launchpad.net/~banshee-team
## Run this command: gpg --keyserver subkeys.pgp.net --recv 6E80C6B7 && gpg --export --armor 6E80C6B7  | sudo apt-key add -
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main

#### Blueman (Source) - https://edge.launchpad.net/~blueman/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
deb-src http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main

#### Chromium Project (Source) - http://code.google.com/chromium/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add -
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

#### Conky (Source) - https://launchpad.net/conky
## Run this command: gpg --keyserver subkeys.pgp.net --recv 95628707 && gpg --export --armor 95628707 | sudo apt-key add -
deb-src http://ppa.launchpad.net/norsetto/ppa/ubuntu jaunty main

#### Gnome-Do (Source) - http://do.davebsd.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 77558DD0 && gpg --export --armor 77558DD0  | sudo apt-key add -
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main

#### Medibuntu (Source) - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src http://packages.medibuntu.org/ jaunty free non-free 

#### OpenOffice.org 3.0 (Source) - https://launchpad.net/~openoffice-pkgs/+archive
## Run this command: gpg --keyserver subkeys.pgp.net --recv 247D1CFF && gpg --export --armor 247D1CFF  | sudo apt-key add -
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main

#### Wine (Source) - http://www.winehq.org/
## Run this command: wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
deb-src http://wine.budgetdedicated.com/apt jaunty main

#### X Updates (Source) - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: gpg --keyserver subkeys.pgp.net --recv AF1CDFA9 && gpg --export --armor AF1CDFA9  | sudo apt-key add -
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main

## Dropbox
deb http://linux.getdropbox.com/ubuntu jaunty main
deb-src http://linux.getdropbox.com/ubuntu jaunty main
deb http://ppa.launchpad.net/0-launchpad-mejlamej-nu/ppa/ubuntu jaunty main

```

---

### Post by Perfect Storm on 2009-09-13
Gee...with so many 3rd-party sources, no wonder it can break dependency. By using 3rd party sources = running a risk.


Edit; You can try getting the libs*-dev from ubuntu package site and eventually downgrade/upgrade; [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by slughappy1 on 2009-09-13
but, but, but, I just used the ubuntu repo generator....

---

### Post by Perfect Storm on 2009-09-13
> **slughappy1 said:**
> but, but, but, I just used the ubuntu repo generator....

It's still 3rd parties which means unsupported/at your own risk.

---

### Post by slughappy1 on 2009-09-13
I realize that. I didn't know that adding 3rd party repos would make some packages not install.

---

### Post by Perfect Storm on 2009-09-13
If the 3rd party sources mess up the dependencies and/or replaces some the package with its own.

You can try disable the 3rd parties and then installing the packages manual from the link I gave previously.

---

### Post by slughappy1 on 2009-09-13
That is a good idea, thanks. I will try that and let you know if it works or not.

---

### Post by mc4man on 2009-09-13
@ slughappy1
look at your screen 1. One of your sources (unless you manually installed it), gave you a git version of libglu1-mesa that is higher than jaunty's. 
None of your sources has that version in a -dev, so the available -dev can't be installed
( that version is what karmic is using.

You can glean a lot from packages.ubuntu ,I just bookmark a random page and search from there

[http://packages.ubuntu.com/jaunty/cdparanoia](http://packages.ubuntu.com/jaunty/cdparanoia)

---

