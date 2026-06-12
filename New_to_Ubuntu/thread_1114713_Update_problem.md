---
title: "Update problem"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by null.byte on 2009-04-03
Hello... I am running Ubuntu 8.10 with GNOME... but I use amarok2, so some KDE stuff is also installed. Today, I saw the update icon, so I clicked it, and I got:

[http://img222.imageshack.us/img222/2936/screenshotf.png](http://img222.imageshack.us/img222/2936/screenshotf.png)

I clicked Partial Upgrade and I got:

[http://img222.imageshack.us/img222/6278/screenshot1c.png](http://img222.imageshack.us/img222/6278/screenshot1c.png)
[http://img222.imageshack.us/img222/4830/screenshot2z.png](http://img222.imageshack.us/img222/4830/screenshot2z.png)

What's happening? :-k

---

### Post by hyper_ch on 2009-04-03
post you /etc/apt/sources.list

---

### Post by null.byte on 2009-04-03
```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ro.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ro.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
deb http://ubuntusatanic.org/hell intrepid main

```

---

### Post by hyper_ch on 2009-04-03
you have 3rd party repos in your sources.list to which you don't have a GPG key imported hence you get that error.

For the PPA repos you can get instructions from my repogen tool. See my sig for it.

---

### Post by bornakke on 2009-04-03
Had the same experience. Ran the partial and basically it removed alle my KDE programs... very strange. Anyone who knows what going on?

Also have this greyed out update manager now..

---

