---
title: "synaptic package installer wont update and i cant sudo apt-get update"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by triiodide on 2011-03-30
E: Type '“deb' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
i have these forums and seen this problem so this is what i get when i type in cat /etc/apt/sources.list this is i get
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
please help!

---

### Post by Locke_99GS on 2011-03-30
The quotes around the last entry in your sources.list shouldn't be there.

Also, automatix hasn't been needed in years, and it's rather out dated. Unless you have some specific need for it, I would both not use it, and remove that entry entirely.

edit: Also in the future if you'd please wrap your terminal paste's in [ code ] tags, it'd make it much easier to read. :)

---

### Post by ~Plue on 2011-03-30
from a terminal or run dialog, run gksu *gedit /etc/apt/sources.list , *then delete the 59th line and save the file. //(reason in the previous post)
then run [I]sudo apt-get update
[/I]

---

### Post by triiodide on 2011-03-30
thank you guys so much that was a really fast reply and fix :P i love these forums. also i a question about ATI cards and linux, i'm using a radeon hd5450 and i have all the drivers installed but on games through wine its not showing i have shader model 3 and some video settings it says unsupported for graphics related reasons... is it just that ati cards don't have the proper support? also it runs games quite slowly compared to windows, if you couldn't tell i am fairly new to linux, been using it for about a week

---

