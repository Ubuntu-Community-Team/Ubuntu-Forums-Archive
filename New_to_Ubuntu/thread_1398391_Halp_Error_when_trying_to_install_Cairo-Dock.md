---
title: "Halp: Error when trying to install Cairo-Dock"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by LiteDrive on 2010-02-04
So, I've been working on getting the .deb file for Cairo to work. In the Ubuntu tutorial it says that I have to grab a few packages first via the terminal. No problem right? 

This is what I punch in:

> 
sudo apt-get install libcairo2 librsvg2-2 libglitz1 libglitz-glx1


This is what I get :/

> E: Type 'wget' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.


I checked the ppa files in the directory the error is showing; it doesn't seem like there's anything wrong with them, unless I'm missing something.

> deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) karmic main ^^^ exactly what's in the 'cairo-dock-team-ppa-karmic.list'

Also, there's another copy of the exact same thing. The only difference is that it says '.save' right after '.list'

I've been running Ubuntu 9.10 (I'm a total beginner) for about 3 weeks now. I love it, but I'm still ignorant to a lot of things; if anyone has any tips or advice, I'd be grateful.

Thanks.

---

### Post by LiteDrive on 2010-02-05
Anyone there? Please, help...

---

### Post by Temposs on 2010-02-05
how did you add the cairo-dock ppa?

---

### Post by chillicampari on 2010-02-05
Could you post your sources.list file (using the forum "code" tag)?

---

### Post by LiteDrive on 2010-02-05
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

deb http://ppa.launchpad.net/compiz/ubuntu karmic main

deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
```

I removed a command I stupidly put in there involving 'wget', via some installation instructions.

As far as the ppa, I added it normally through software sources. I'm not sure if I did anything wrong here, besides the 'wget' command though. The main problem is that this error is still active and it's keeping me from accessing my package/update/software manager(s).

---

### Post by chillicampari on 2010-02-05
> **LiteDrive said:**
> I removed a command I stupidly put in there involving 'wget', via some installation instructions.

As far as the ppa, I added it normally through software sources. I'm not sure if I did anything wrong here, besides the 'wget' command though. The main problem is that this error is still active and it's keeping me from accessing my package/update/software manager(s).

  My guess would be you might have fixed it by removing that (if you removed it from the source file, not just the copy posted). But if you're still getting the error, not sure why.

---

### Post by Leppie on 2010-02-05
after removing the command from sources.list, did you run the update function?
```
sudo apt-get update
```

---

### Post by LiteDrive on 2010-02-05
Sweet! Everything worked great.

Thank you much, everyone. 

:)

---

### Post by Leppie on 2010-02-05
glad it's working again.

if this is resolved, set the thread to solved using the thread tools.

---

