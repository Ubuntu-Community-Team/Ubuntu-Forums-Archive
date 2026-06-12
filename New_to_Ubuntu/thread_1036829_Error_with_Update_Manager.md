---
title: "Error with Update Manager"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by SillySod on 2009-01-11
I'm having a problem with the Update Manager. I can download the updates without any trouble, but I don't seem to be able to update the package information.  If I try to check this, I get an error box with the following:

```

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network
problems. If available an older version of the failed index will be used. Otherwise the
repository will be ignored.  Check your network connection and ensure the repository address
in the preferences is correct.

Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz 
404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.


```

Can anyone help?

---

### Post by RealPSL on 2009-01-11
It seems as if it is trying to access data from an older release of Ubuntu. What release are you running? Would you mind posting the output of ```
cat /etc/apt/sources.list
```

---

### Post by SillySod on 2009-01-14
OK, here we go:

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary universe

# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main

```

Many thanks.

---

### Post by avtolle on 2009-01-14
You need to eliminate the reference to "hoary"(last line before Pulse Aduio). Best way is to edit the sources list to comment it out (put # before the line) or by deleting it. What I'd do is go into the terminal and ```
sudo nano /etc/apt/sources.list
```scroll down to the offending line, comment it out, then Ctrl o to save, Enter to verify the default name of the file, and Ctrl X to exit. Then try```
sudo apt-get update && sudo apt-get upgrade
``` and see if works for you.

---

### Post by SillySod on 2009-01-18
That's done the trick, I'm all up to date now!

Many thanks.

P.S. How do I thank people and set the thingy to "Solved"?

---

