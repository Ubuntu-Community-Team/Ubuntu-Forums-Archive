---
title: "weird things going when I run Synaptic"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Jonas thomas on 2009-06-07
A couple of nights ago I started to get some error messages about some code::block libraries (not sure if that has anything going on with that...

Now I tried uninstalling code::blocks completely and this error is popping up.
E: cron: subprocess post-installation script returned error exit status 1
E: acpid: subprocess post-installation script returned error exit status 1

The acpid error has been popping up for month's.  I think that has something to do about shutting down the hard drive after being idle.  (I would be nice if it didn't error out but, it still seems to be working.

This cron error thing is something new and might be causing me some pain...

Do I need to get that straighten out before I try re-loading code::blocks...

Did anyone else just start having this pop up on them?....

---

### Post by kwacka on 2009-06-07
Do you have any non-Ubuntu repositories enabled (e.g. debian)?

---

### Post by Jonas thomas on 2009-06-07
> **kwacka said:**
> Do you have any non-Ubuntu repositories enabled (e.g. debian)?

Why yes I do... Do you think that has something to do with it??
Below is what I have in /etc/apt/sources.list
Do you see anything that maybe creating the issue??
How critical are cron and acpid? What would be the consequences if I just uninstalled them??


```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

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
deb http://www.opennovation.org/ubuntu hardy main contrib non-free
##deb http://www.backports.org/debian etch-backports main contrib non-free
deb http://archive.ubuntu.com/ubuntu hardy-backports main universe multiverse restricted

## added this because of my c++ mplayer issue 9-13-08 see ubuntu forums
deb http://archive.ubuntu.com/ubuntu hardy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy universe multiverse
deb http://lgp203.free.fr/ubuntu/ hardy universe
deb http://apt.wxwidgets.org/ hardy-wx main

# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main

#Different Pulse Audio Fixes http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+connection+refused
#deb http://ppa.launchpad.net/zman0900/ubuntu hardy main
#deb-src http://ppa.launchpad.net/zman0900/ubuntu hardy main


```

---

### Post by Jonas thomas on 2009-06-07
Thinks started getting weird around friday..
Hear's my update from friday..
Commit Log for Fri Jun  5 05:37:16 2009


Upgraded the following packages:
codeblocks (8.02svn5602-0ubuntu1~hardy) to 8.02svn5616-0ubuntu1~hardy
codeblocks-common (8.02svn5602-0ubuntu1~hardy) to 8.02svn5616-0ubuntu1~hardy
codeblocks-contrib (8.02svn5602-0ubuntu1~hardy) to 8.02svn5616-0ubuntu1~hardy
codeblocks-contrib-common (8.02svn5602-0ubuntu1~hardy) to 8.02svn5616-0ubuntu1~hardy
cron (3.0pl1-100ubuntu2) to 3.0pl1-100ubuntu2.1
cupsys (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
cupsys-bsd (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
cupsys-client (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
cupsys-common (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
libcodeblocks0 (8.02svn5602-0ubuntu1~hardy) to 8.02svn5616-0ubuntu1~hardy
libcupsimage2 (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
libcupsys2 (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
libwxsmithlib0 (8.02svn5602-0ubuntu1~hardy) to 8.02svn5616-0ubuntu1~hardy
pm-utils (0.99.2-3ubuntu10) to 0.99.2-3ubuntu10.1

---

