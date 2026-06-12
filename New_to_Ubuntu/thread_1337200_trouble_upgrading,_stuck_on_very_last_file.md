---
title: "trouble upgrading, stuck on very last file"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by rocka on 2009-11-25
Hi,

I attempted to upgrade tonight, but the download failed on the very last file - 1538 of 1538, IIRC.

The error message was:
```
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.9.8-1ubuntu2_all.deb Hash Sum mismatch
```

I tried it 3 times with the same result.

any ideas?
;)

---

### Post by ukripper on 2009-11-25
I'd suggest better option is to do fresh install. Upgrade had quite a lot of problems from 9.04 to 9.10. Even if you resolve this by changing different repo other problem may show up.

With fresh install you would just need to copy your data back to your home. 

*Now to your problem:*
post your sources.list here

```
gedit /etc/apt/sources.list
```

or just go to system-->Administration-->Software sources and  switch your repos to main server

---

### Post by Sealbhach on 2009-11-25
For the time being, unselect it in the update manager. You only need it if you have a HP printer, as far as I know. 

Then try the suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=1237255](http://ubuntuforums.org/showthread.php?t=1237255)

.

---

### Post by rocka on 2009-11-25
ok then...
sources.list:
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
```

---

### Post by ukripper on 2009-11-25
looks like you trying to upgrade 8.10 to 9.10. Not sure if that is possible without upgrading to 9.04.

---

### Post by rocka on 2009-11-25
> **Sealbhach said:**
> For the time being, unselect it in the update manager. 
.

Hi,

I didn't see any option to select/unselect anything. I just clicked System/Administration/Update Manager, then, noticing the notice at the top saying 9.10 was available, I clicked "Upgrade". It then pretty much went right ahead, it didn't give me any choices to select/unselect anything.

---

### Post by ukripper on 2009-11-25
> **rocka said:**
> Hi,

I didn't see any option to select/unselect anything. I just clicked System/Administration/Update Manager, then, noticing the notice at the top saying 9.10 was available, I clicked "Upgrade". It then pretty much went right ahead, it didn't give me any choices to select/unselect anything.

Bizarre, if you were running 8.10, update manager should say 9.04 upgrad is available not 9.10.

Are you using 8.10 or 9.04 right now?

---

### Post by rocka on 2009-11-25
> **ukripper said:**
> looks like you trying to upgrade 8.10 to 9.10. Not sure if that is possible without upgrading to 9.04.

no, I'm on 9.04 now.
The original install on this machine was 8.10; the upgrade from 8.10 to 9.04 went without a hitch.

---

### Post by ukripper on 2009-11-25
> **rocka said:**
> no, I'm on 9.04 now.
The original install on this machine was 8.10; the upgrade from 8.10 to 9.04 went without a hitch.

ok in that case just change your software sources to point to main server as i mentioned earlier.

---

### Post by rocka on 2009-11-25
> **ukripper said:**
> ok in that case just change your software sources to point to main server as i mentioned earlier.

thanks a lot - that worked :)


fantastic help - thanks everyone who replied.

---

### Post by ukripper on 2009-11-25
great. Please mark this thread as solved from Thread tools.

---

