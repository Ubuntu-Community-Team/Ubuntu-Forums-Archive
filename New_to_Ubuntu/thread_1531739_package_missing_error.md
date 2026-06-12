---
title: "package missing error"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by libihero on 2010-07-15
i get this error in the terminal when i try to update:
```
Err http://www.sourceslist.eu lucid/main Packages
  404  Not Found
Err http://www.sourceslist.eu lucid/non-free Packages
  404  Not Found
Fetched 2,446B in 24s (99B/s)
W: Failed to fetch http://www.sourceslist.eu/repo/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://www.sourceslist.eu/repo/ubuntu/dists/lucid/non-free/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

how can i fix it?

---

### Post by Zorgoth on 2010-07-15
That is probably an error with your internet connection.  To fix it - try again in a few minutes, and then in an hour or so, and/or restart your connection/router.

It could also be that those URLs are temporarily down.

---

### Post by fooman on 2010-07-15
try another server...open software sources,  go to > system > administration > software sources

under the "ubuntu software" tab....try clicking the down arrow next to "download from"

choose "main server" or click "other",  then "select best server" and it should find the best one for you.

hope that helps.

---

### Post by libihero on 2010-07-16
i still get the error on an excellent connection and changing the server :S

---

### Post by fooman on 2010-07-16
please post the contents of:

```
/etc/apt/sources.list
```

---

### Post by neu5eeCh on 2010-07-17
Ditto. The same problem here too.

---

### Post by libihero on 2010-07-18
i was able to fix it by commenting out the last thing in my source list, but i dont kno if it was important :S

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid main restricted
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-updates main restricted
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid universe
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid universe
deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-updates universe
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid multiverse
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid multiverse
deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-updates multiverse
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-security main restricted
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-security main restricted
deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-security universe
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-security universe
deb http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-security multiverse
deb-src http://ftp-stud.hs-esslingen.de/ubuntu/ lucid-security multiverse
deb http://ppa.launchpad.net/zekr/ubuntu lucid main
deb http://ppa.launchpad.net/ajmitch/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/ajmitch/ppa/ubuntu lucid main

# deb http://www.sourceslist.eu/repo/ubuntu lucid main non-free
```

---

