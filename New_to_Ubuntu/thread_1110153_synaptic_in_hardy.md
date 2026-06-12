---
title: "synaptic in hardy"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by DarinB on 2009-03-29
E: Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

what do i do to fix synaptic??????????????????

---

### Post by Sidewinder1 on 2009-03-29
Your subject is "Synaptic in **Hardy**", but your profile lists **Intrepid Ibex**, perhaps that's the problem?

---

### Post by DarinB on 2009-03-29
this is for a friends computer that i installed hardy on. good catch so any ideas

---

### Post by tripolitan on 2009-03-29
Nothing wrong with Synaptic, what does line 1 in source list say?
possible problems:

-Malformed address.>>get the proper address

-Site not found (because site is down or malformed address)>>get proper address, ping the repository.

if all fails, please post the content of your /etc/apt/sources.list

---

### Post by DarinB on 2009-03-29
i have no clue what this means? in relation to the error message above

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by oldos2er on 2009-03-29
> **DarinB said:**
> E: Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

what do i do to fix synaptic??????????????????

```
gksu gedit /etc/apt/sources.list.d/pidgin-ppa.list
```

 At the beginning of line 1, add a comment mark #
 
 Save and exit the file, then run
```
sudo apt-get update
```

---

### Post by tripolitan on 2009-03-29
You have installed a repository that may contain a malformed address.
Open synaptic and search for pidgin-ppa, then remove it.

Alternatively, as root, you may want to open /etc/apt/sources.list.d/pidgin-ppa.list and manually fix the address. If you can't fix the address, post it.

---

### Post by DarinB on 2009-03-29
thank you the # removed the line thanks 

i need to reinstall pidgin i tried to remove the one that came with it and add the latest version and now i can't get anything to work,,,,this is a freinds pc with hardy too bad i should have never messed with it. 
i tried empathy from the repos but it says it needs backend protocols adn i don't know what to do with that either
HELP she is pissed!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by hyper_ch on 2009-03-29
if you need/want more 3rd party repos, you can check out the tool in my sig :)

---

### Post by tripolitan on 2009-03-29
Aha! you managed to piss someone off! What was wrong with the original version of Pidgin? what does the less-tested developer version have that the older-stable version doesn't and is it worth the hassles?. I have followed that rationale and stayed trouble free, since the first Ubuntu LTS.

I don't recommend straying away from original distro supported packages but if you must, here is the Hardy-backports, they have version 2.5.2 (at your own risk) if you really need it!:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main universe multiverse restricted

I would purge the old one and any other related files/libs first. If you already have deborphan (recommended package for synaptic)installed, try sudo orphaner and pick all the orphaned libs (dont remove libstdc5++ and any gstreamer libs)

---

