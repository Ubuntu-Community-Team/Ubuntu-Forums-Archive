---
title: "Problem with package manager"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by The-Red-Baron on 2009-11-25
hello there.. new user too... have the same problems with the synaptic package... thanks.... here´s my list:

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by bapoumba on 2009-11-26
@ The-Red-Baron: what is your exact error ?

Please paste the output to:
```
sudo apt-get update
```

Your error may be completely unrelated to this thread. I'm going to split it to its own thread.

---

