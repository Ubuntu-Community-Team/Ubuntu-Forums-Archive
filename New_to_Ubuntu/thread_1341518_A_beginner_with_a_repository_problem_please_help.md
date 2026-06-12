---
title: "A beginner with a repository problem please help"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Dream Figther on 2009-11-29
I have a problem with the repository.
I cant go in Synaptic Manager nor update any thing on the terminal.. 
It all happen when i tried to download some packages from the terminal i think some files are corrupted..

THIS IS THE ERROR THAT SHOWS UP WHEN I OPEN SYNAPTIC:


E: Type '\u201cdeb' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

What do i linux buddies.?!!:KS

---

### Post by markjensen on 2009-11-29
Did you manually edit that file at some point in time?

The fault it is posting is clearly complaining about line 54 containing something it cannot deal with: "\u201cdeb"

You can either post the file, and have us look at it, or try fixing (commenting out with a #) it yourself.  Maybe it can be fixed within synaptic.

Try starting synaptic, click the Settings menu, and select Repositories.

In the tabbed interface you are presented, pick the "Other Software" tab.  See if you can find the "\u201cdeb" entry and un-check it.

---

### Post by sandyd on 2009-11-29
> **Dream Figther said:**
> I have a problem with the repository.
I cant go in Synaptic Manager nor update any thing on the terminal.. 
It all happen when i tried to download some packages from the terminal i think some files are corrupted..

THIS IS THE ERROR THAT SHOWS UP WHEN I OPEN SYNAPTIC:


E: Type '\u201cdeb' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

What do i linux buddies.?!!:KS
Open a terminal (Applications -> Accessories -> Terminal)
and copy and paste this in
```

cat /etc/apt/sources.list >> ~/Desktop/aptsources.txt

```
then attatch the aptsources.txt file (its on your desktop) to here.

---

### Post by Dream Figther on 2009-11-29
I get this maybe i need to delete something.?

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps #GetDeb
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main

---

### Post by markjensen on 2009-11-29
I see two lines in quotes down at the bottom area.   You should be able to just remove the quotes and you will probably be ok.

It looks like someone provided two lines to add, and had them quoted, and you might have copied the quotes into the file, too?


EDIT:  Let me add, you need to be **root** to modify that file.   Perform the following command:
**gksudo gedit /etc/apt/sources.list**


EDIT #2:  Ahhhh!  /u201 must be "unicode" for the quote symbol!  (a lightbulb goes off in my head)

---

### Post by Dream Figther on 2009-11-29
O.k.!! I got it.! DAM it was sooo easy.!! Thank you[:]("http://ubuntuforums.org/member.php?u=717412")
CARLEE & MARKJENSEN.!!!
Take Care.!!:KS
[ ]("http://ubuntuforums.org/member.php?u=717412")

---

