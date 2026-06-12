---
title: "Hardy Add/Remove running slow"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2009-01-16
Ok for a couple days now my computer has been running really slow.  Especially in Add/Remove and Synaptic.  I've tried googling this problem, and I found an archived thread back in August that Ubuntu was having server issues.  Does anyone know if this is going on now?  Right now everything is downloading in just Bps!?

---

### Post by taurus on 2009-01-16
What happens to your download speed if you run it from a terminal with 

```
sudo apt-get update
sudo apt-get upgrade
```
What server are you using?

```
cat /etc/apt/sources.list
```

---

### Post by Nazty_Nayt on 2009-01-16
Not sure what server I'm on, here's what I got when running that command...

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

```

And everything's up to date, after running apt get, I still get the same speed.

---

### Post by taurus on 2009-01-16
The Canadian server has been acting up (or down) for a while now.  So, go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and pick another server.  You can use the Main Server if you want.  That should improve your downloading speed (repos) a lot.  Don't forget to click the Reload button.

---

### Post by Nazty_Nayt on 2009-01-16
I think something might be wrong with my system, it's not recognizing me as the administrated user for some reason!?  Says I'm starting without those privilages.

---

### Post by Nazty_Nayt on 2009-01-16
Ok, well I restarted, and it let me in (don't know what that was all about).  I switched to the main server, and it's working much better now, thanks taurus!

:guitar:

---

