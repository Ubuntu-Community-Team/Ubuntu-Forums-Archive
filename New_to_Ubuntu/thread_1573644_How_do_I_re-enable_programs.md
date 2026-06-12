---
title: "How do I re-enable programs?"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by greenleaves123 on 2010-09-13
I tried searching for this, but I couldn't come up with a search that yielded results I wanted.

I just upgraded Ubuntu from 8.10 to the next version and in the process it said it disabled some things.

How do I re-enable them?

---

### Post by TNT1 on 2010-09-13
what did it disable? why do you want to enable them? how did you upgrade, are you on 9.04 now?

---

### Post by greenleaves123 on 2010-09-13
Yeah, I'm on 9.04 now. I think it disabled 3rd party something or other, I'm not sure. I had just gotten my nutrition tracking software working before the upgrade, but now it doesn't work. I see the files for it, but they don't register or something.

---

### Post by TNT1 on 2010-09-13
Post:
```
cat /etc/apt/sources.list
```

---

### Post by greenleaves123 on 2010-09-13
jenny@jenny-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty main restricted
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-updates main restricted
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty universe
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty universe
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-updates universe
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty multiverse
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty multiverse
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-updates multiverse
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-security main restricted
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-security main restricted
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-security universe
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-security universe
deb [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-security multiverse
deb-src [ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/](ftp://ftp.cs.mun.ca/pub/mirror/ubuntu/) jaunty-security multiverse
jenny@jenny-laptop:~$

---

### Post by TNT1 on 2010-09-13
What's the software that doesn't work?

---

### Post by greenleaves123 on 2010-09-13
The CRON-O-meter

---

### Post by TNT1 on 2010-09-13
That's a java app? Does java run fine with other apps since upgrade?

---

### Post by greenleaves123 on 2010-09-13
I don't know, how can I tell?

---

### Post by greenleaves123 on 2010-09-13
I decided to just download it again and install it and now it works.

---

