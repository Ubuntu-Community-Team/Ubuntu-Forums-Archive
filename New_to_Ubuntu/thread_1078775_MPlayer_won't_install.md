---
title: "MPlayer won't install"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by SINZAR on 2009-02-23
Hey guys, I can't get mplayer to install. 

```
ben@benuntu:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
           Depends: libggi2 (>= 1:2.2.2) but it is not going to be installed
           Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
           Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-2.1ubuntu1 is to be installed
           Depends: libmp3lame0 (>= 3.98) but it is not installable
           Depends: libopenal1 (>= 1:1.3.253) but it is not installable
           Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
           Depends: libspeex1 (>= 1.2~beta3-1) but 1.1.12-3ubuntu0.8.04.1 is to be installed
           Depends: libx264-59 (>= 1:0.svn20080408) but it is not installable
E: Broken packages
ben@benuntu:~$ 

```

Here's my sources.list

```
ben@benuntu:~$ sudo vi /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse #Added by software-propertiesdeb http://security.ubuntu.com/ubuntu/ hardy-security universe main restricted multiversedeb-src http://security.ubuntu.com/ubuntu/ hardy-security universe main restricted multiverse #Added by software-propertiesdeb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main restricted multiversedeb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main restricted multiverse #Added by software-properties
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

Any suggestions?

---

### Post by Crafty Kisses on 2009-02-23
Try updating, so run the following:
```
sudo apt-get update
```
Once you have done that try installing mplayer again.

---

### Post by ptn107 on 2009-02-23
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse #Added by software-propertiesdeb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main restricted multiversedeb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main restricted multiverse #Added by software-propertiesdeb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main restricted multiversedeb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main restricted multiverse #Added by software-properties


These lines are for Ubuntu 8.04, not for 7.10.  You should remove them from your sources.list, as mixing repositories of different versions is a recipe for disaster.

---

### Post by SINZAR on 2009-02-24
> **Codename said:**
> Try updating, so run the following:
```
sudo apt-get update
```
Once you have done that try installing mplayer again.

> **ptn107 said:**
> These lines are for Ubuntu 8.04, not for 7.10.  You should remove them from your sources.list, as mixing repositories of different versions is a recipe for disaster.

Thanks for the tips fellas. I'm still unable to install mplayer though, same error.

---

### Post by llamabr on 2009-02-24
Do them in the other order.  First, clean out your sources.list, then do apt-get update, then try to install.

---

### Post by SINZAR on 2009-02-25
> **llamabr said:**
> Do them in the other order.  First, clean out your sources.list, then do apt-get update, then try to install.

Gave it a try but no dice.

Just as a note, I am running Hardy so I cleared out the gutsy references rather than removing the hardy references. Why is it still trying to get older packages?

---

### Post by handy on 2009-02-25
You could try apt-get -f

It may fix your broken dependencies, as that is what it is supposed to do.

---

### Post by gandaran on 2009-02-25
> Just as a note, I am running Hardy so I cleared out the gutsy references rather than removing the hardy references. Why is it still trying to get older packages?
then your sources.list is a mess, are you sure it's hardy you running? it looks like gutsy, for hardy there are some repository's missing!

---

### Post by Michael.Godawski on 2009-02-25
hi,
let's check with
```
lsb_release -a  
```
what release you are running.

---

### Post by SINZAR on 2009-02-25
> **gandaran said:**
> then your sources.list is a mess, are you sure it's hardy you running? it looks like gutsy, for hardy there are some repository's missing!

```
ben@benuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy

```

It was a originally a gutsy install from cd and then a distro upgrade was performed which may explain the mess that is my sources.list. Also, when it was installed from cd there was no internet which is why there was all those failures so I had to go in manually and uncomment each entry out.

---

### Post by llamabr on 2009-02-25
So before you change anything else, you're running hardy, but your sources.list is full of gutsy?

You never did a dist-upgrade since doing all that uncommenting you talked about?

---

### Post by SINZAR on 2009-02-25
When I originally set up the machine I used the gutsy cd, fixed the sources.list and then performed the distro upgrade to hardy. Since then I haven't had any issues with updates (that I know of) and haven't had any issue installing any programs, other than this current one with mplayer.

---

### Post by SINZAR on 2009-02-26
bump

---

### Post by SINZAR on 2009-02-27
Anybody want to be a last minute hero before I let this thread die and go on without mplayer?

---

### Post by gandaran on 2009-02-27
SINZAR
the fix for you should be easy, just ask someone that uses ubuntu 8.04 for the full sources.list, copy/replace it in your system ( I can't help you here, I'm running 8.10 so no hero!) or why not do a clean reinstall of ubuntu?

---

