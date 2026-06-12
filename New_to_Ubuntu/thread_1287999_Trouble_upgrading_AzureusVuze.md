---
title: "Trouble upgrading Azureus/Vuze"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by kelliegirl09 on 2009-10-10
Hey everyone, super newbie here and I'm having trouble upgrading my current version of Azureus to the newer version (Waffles no longer allows my version to be used).

I downloaded the newest version but when I do sudo apt-get install I get this message:

E:  Couldn't find package Vuze

Any help you guys give me will have to be very basic step by step stuff.  Thanks!

Oh and I have the screwy netbook version of ubuntu, 8.04 I think.

---

### Post by sandyd on 2009-10-10
sudo apt-get install vuze
WITHOUT the capital.

---

### Post by sandyd on 2009-10-10
p.s. when vuze starts and asks for an update, don't update it.

instead, disable the updateing through the vuze options.
(updating vuze is impossible unless your running with elevated user privelages)

---

### Post by kelliegirl09 on 2009-10-10
I'm not using any capitals.  Still the same error message.

---

### Post by 3rdalbum on 2009-10-10
> **kelliegirl09 said:**
> I'm not using any capitals.  Still the same error message.

Make sure all your repositories are enabled in System > Preferences > Software Sources, and if they are then try reloading the package list by clicking the Reload button in Synaptic, or typing this command:

```
sudo apt-get update
```

---

### Post by sandyd on 2009-10-10
enable universe repositories...

if you don't wanna enable them... then downloading and running this will install vuze.
[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/vuze_4.2.0.8-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/vuze_4.2.0.8-1ubuntu1_all.deb)

see if
```

sudo apt-get install azureus java-wrappers libswt-cairo-gtk-3.4-jni libswt-gnome-gtk-3.4-jni libswt-gtk-3.4-java libswt-gtk-3.4-jni libswt-mozilla-gtk-3.4-jni


```works.

---

### Post by kelliegirl09 on 2009-10-10
When I do sudo apt-get update it says I already have the updated versions for everything.  What I'm trying to do is just install the newer version that I have downloaded already.  I currently have Azureus 2.0 or something and I'm trying to install 3.0.5.0.  I downloaded 3.0.5.0 from the website, then i do sudo apt-get install vuze and I get that error message saying it can't find the package.  In the software sources all the repositories are enabled but there are no repositories for vuze.

---

### Post by sandyd on 2009-10-10
if you noticed, vuze is only a metapackage for azureus.

if you install azureus from the repos nowadays, you get the same thing as installing vuze from the repos.

---

### Post by kelliegirl09 on 2009-10-10
Ok I didn't see your previous reply.  I followed that link and I get this error:

Dependency is not satisfiable" libswt-cairo-gtk-3.4-jni

then I put in that command and I get this error:

E: Couldn't find package java-wrappers

---

### Post by sandyd on 2009-10-10
i rest my case.

run this
```

cd /opt
sudo wget http://cache2.vuze.com/files/Vuze_Installer.tar.bz2
sudo tar -jxvf Vuze_Installer.tar.bz2
sudo chmod -R 777 vuze
sudo ln /opt/vuze/vuze /usr/bin/vuze
sudo rm Vuze_Installer.tar.bz2

```to run vuze,
```

vuze

```p.s. i composed this on the spot so there may be typos...

STOP: don't do this yet! see my next post.

---

### Post by sandyd on 2009-10-10
ok. there is something seriously wrong now.

can you do 
```

gedit /etc/apt/sources.list

```

and paste all the stuff in that file here?

---

### Post by kelliegirl09 on 2009-10-11
Thanks so much in advance for all your help! I really appreciate it.  Below is the sources.list file....there is still some qbittorrent stuff I pasted in there when I was trying to install qbittorrent and I was having the same exact problem and getting the same exact E: message.



deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

##medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

---

### Post by sandyd on 2009-10-11
> **kelliegirl09 said:**
> Thanks so much in advance for all your help! I really appreciate it.  Below is the sources.list file....there is still some qbittorrent stuff I pasted in there when I was trying to install qbittorrent and I was having the same exact problem and getting the same exact E: message.



deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

##medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

seems like canonical hasn't put vuze into its netbook repos.
you now have two options.

1. replace the sources.list with this one temperirily
```

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

##medibuntu
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free

deb http://hydr0g3n.free.fr/qbittorrent/feisty/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/feisty/ ./

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main
deb http://packages.medibuntu.org/ hardy free non-free
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://se.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some appligbtions which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from gbnonigbl's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by gbnonigbl and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
# deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu hardy main
# deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu hardy main
# deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main
deb http://download.virtualbox.org/virtualbox/debian hardy non-free
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu hardy main
deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu hardy main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu hardy main
deb http://wine.budgetdedicated.com/apt hardy main
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu hardy main
deb http://ppa.launchpad.net/neversfelde/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/neversfelde/ppa/ubuntu hardy main
deb http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu hardy main
deb-src http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu hardy main
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu hardy main
# deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu hardy main
deb http://ppa.launchpad.net/giftwrap/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/giftwrap/ppa/ubuntu hardy main

```then
enter this in the terminal
```

sudo apt-get update
sudo apt-get install vuze

```Then, turn your sources.list back to normal
```

gedit /etc/apt/sources.list

```and replace everything with
```

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

##medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

```
or 2.

uninstall the current version of ubuntu you have and install the normal version of ubuntu instead of the version dell gives .

advise you go for #2.
its easier, and you won't have problems in the future.

---

### Post by kelliegirl09 on 2009-10-11
My friend downloaded the normal version of ubuntu, but he said he was unsure of whether or not it would bog down my computer if he installed it.  So you think I should just uninstall this crappy netbook version and put the normal version on?

---

### Post by sandyd on 2009-10-11
> **kelliegirl09 said:**
> My friend downloaded the normal version of ubuntu, but he said he was unsure of whether or not it would bog down my computer if he installed it.  So you think I should just uninstall this crappy netbook version and put the normal version on?
i ran karmic on a dell CSx just as a proof-of-concept.

its a 500mhz machine with 384 mb of ram. 
and ubuntu still moves resonably fast.

read
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by stuart221 on 2009-10-18
Go to getdeb.net and download vuze

---

### Post by serein on 2009-10-25
> **stuart221 said:**
> Go to getdeb.net and download vuze
haha. ****. just looked through this thread. those previous tips where pretty good if you want nothing to make sense and are willing to **** up your os...
that took a while. getdeb - quick and easy. but, it's even easier to download it from vuze.com, there's never any problems updating with vuze's internal updater then... and  it's just to extract and start the app...

---

