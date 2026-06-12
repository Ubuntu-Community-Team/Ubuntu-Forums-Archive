---
title: "Error when checking for updates"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Almeida1 on 2010-05-11
Hi 

I am currently using Ubuntu 9.10 but when I go to System -> Administrator -> UPdate Manager and check for updates I get the following error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.30 80]

Does anyone know how I can fix this?

---

### Post by plucky on 2010-05-11
> **Almeida1 said:**
> Hi 

I am currently using Ubuntu 9.10 but when I go to System -> Administrator -> UPdate Manager and check for updates I get the following error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.30 80]

Does anyone know how I can fix this?

Are you using Edgy Eft? 

As that is what it is trying to find,and those repositories have closed down as that version is no longer supported.

Post output from a terminal of ```
cat /etc/apt/sources.list
```

Good Luck

---

### Post by Almeida1 on 2010-05-12
> **plucky said:**
> Are you using Edgy Eft? 

As that is what it is trying to find,and those repositories have closed down as that version is no longer supported.

Post output from a terminal of ```
cat /etc/apt/sources.list
```

Good Luck

Thanks for the reply. Here is my output:

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
# deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main

# deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main

```

---

### Post by plucky on 2010-05-12
```
deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main
```


Those two lines are the problem.Either use **System > Administration > Software Sources** and un-tick those repositories and then reload.

Or

Open a terminal and ```
gksudo gedit /etc/apt/sources.list
``` and delete those two lines.

Whichever you are most comfortable with.

Good Luck

---

### Post by Almeida1 on 2010-05-12
> **plucky said:**
> ```
deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main
```


Those two lines are the problem.Either use **System > Administration > Software Sources** and un-tick those repositories and then reload.

Or

Open a terminal and ```
gksudo gedit /etc/apt/sources.list
``` and delete those two lines.

Whichever you are most comfortable with.

Good Luck

That has fixed it! Thanks a lot.

---

