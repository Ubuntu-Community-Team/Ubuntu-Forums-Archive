---
title: "Repository problem"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by bvpainter on 2010-01-11
When I do a sudo apt-get update or try to use synaptic I get the following message" E: Type ‘n’ is not known on line 1 in source list /etc/apt/sources.list.d/docky-core-ppa-karmic.list"

How do I correct this. I've tried editing /etc/apt/sources.list.d/docky-core-ppa-karmic.list in gedit but cannot save alterations as it is a read-only file.

Please help. This all started when I tried to install Docky.

---

### Post by howefield on 2010-01-11
Open the sources.list with sudo and you'll be able to save.

From terminal type,

```
sudo gedit /etc/apt/sources.list
```

Or post the contents here if you want some help before editing.

---

### Post by Cheesemill on 2010-01-11
> **howefield said:**
> Open the sources.list with sudo and you'll be able to save.
 
From terminal type,
 
```
sudo gedit /etc/apt/sources.list
```
 
Or post the contents here if you want some help before editing.
 
 
You should never use sudo for GUI apps. Use:
```
 
gksudo gedit /etc/apt/sources.list

```instead.

---

### Post by howefield on 2010-01-11
> **Cheesemill said:**
> You should never use sudo for GUI apps. Use:

That's twice in a week I've done that, need to be more careful.

---

### Post by bvpainter on 2010-01-11
> **howefield said:**
> Open the sources.list with sudo and you'll be able to save.

From terminal type,

```
sudo gedit /etc/apt/sources.list
```

Or post the contents here if you want some help before editing.

I cannot find this entry inmy sources list which follows

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://nl2.archive.ubuntu.com/ubuntu/](http://nl2.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
# deb [http://ppa.launchpad.net/project-neon/ppa/ubuntu](http://ppa.launchpad.net/project-neon/ppa/ubuntu) jaunty main deb-src [http://ppa.launchpad.net/project-neon/ppa/ubuntu](http://ppa.launchpad.net/project-neon/ppa/ubuntu) jaunty main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free

# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main

deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main

Can you help further.

---

### Post by snowpine on 2010-01-11
```
gksu gedit /etc/apt/sources.list.d/docky-core-ppa-karmic.list
```

---

### Post by bvpainter on 2010-01-11
This seems to have worked. Thanks.

---

### Post by Soul-Sing on 2010-01-11
I don't know but you have [COLOR="Red"]karmic and jaunty[/COLOR] sources in your sources.list active:

## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

---

