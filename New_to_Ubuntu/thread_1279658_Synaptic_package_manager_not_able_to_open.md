---
title: "Synaptic package manager not able to open"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by dhanabalan_svks on 2009-10-01
hello friends,
i faced below problem .i am using ubunthu 9.04 

I am not able to open Synaptic package manager.if i open it gives error message as follows..

E: Type '‘deb-src' is not known on line 43 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


My source.list content below 


# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main
‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main



Please help me ..

Thanks,
Dhanabalan.cs,:confused:

---

### Post by bruno9779 on 2009-10-01
this line

```
‘deb-src http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu jaunty main’
```

is not good. Remove ' from the beginning and the end of it.

while we are at it, I pass you a great link for sources list

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

---

### Post by dhanabalan_svks on 2009-10-01
Thanks friend,

But there are four same lines appear, which i have to delete?

---

### Post by overdrank on 2009-10-01
Moved to Absolute Beginner Talk

---

### Post by dhanabalan_svks on 2009-10-01
Thanks dear

I am able to access my Synaptic package manager 

Thanks for your help

---

### Post by bruno9779 on 2009-10-01
Good to hear.

please mark the thread as solved

---

