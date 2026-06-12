---
title: "[SOLVED] I keep getting this error during Update Manager"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-12-14
Every time I run Update Manager, I keep getting this: ```
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/mainecho/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/deb/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas? I get another one sometimes that says something about "duplicate sources". I know how to edit the sources list as GK, is there something I can do to fix these issues?

---

### Post by DougieFresh4U on 2008-12-14
Would you please post your sources list for us. You may have some of the same lines twice in your sources list.
Also have you tried doing updates via the terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by BastardNamban on 2008-12-14
Thanks. Here's what I got: ```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://jp.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jp.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://jp.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ hardy universe
deb http://jp.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://jp.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://jp.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://jp.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy mainecho deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```

Also, I'll try your sugguestion from terminal.

SIDE QUESTION: In regards to terminal commands, it seems my life would be a lot easier if I could remember all those nifty commands people quote to me like magic language. Is there a good way to learn them? How do you all learn/remember them?

---

### Post by DougieFresh4U on 2008-12-14
you have this 3 times in your sources list
**deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main**
In remembering commands, I do not know a way to remember. I still have to ask for some commands, but I always update with terminal. This way I can see what is happening  and have control over it, so the commands I gave to you are always used by me when updating. I do keep a little index card nearby that I have jotted commands down as I see them posted, knowing that one day I may need that command.

---

### Post by zvacet on 2008-12-14
@ **BastardNamban**

> it seems my life would be a lot easier if I could remember all those nifty commands people quote to me like magic language. Is there a good way to learn them?

[http://linuxcommand.org/]("http://linuxcommand.org/")

[http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")

---

### Post by BastardNamban on 2008-12-14
Thank you both. Those are a great help!

---

