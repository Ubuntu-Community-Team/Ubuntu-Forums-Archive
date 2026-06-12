---
title: "Amarok 2.0"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-02
Can anyone help me to install this on Ubuntu? 1.4 is in repos, but I want to try out the newer version.

thanks!

---

### Post by Silare Alvreon VI on 2008-12-02
What repos do you have enabled at the moment?

---

### Post by adobrakic on 2008-12-02
I have Linux Mint 6.0 RC1, actually, heh, but yeah..

```

## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 6 Felicia (stable) +++
deb http://packages.linuxmint.com/ felicia main upstream import 

## +++ Backports (not as stable) +++
# deb http://packages.linuxmint.com/ felicia backport 

## +++ Community (not as stable) +++
# deb http://packages.linuxmint.com/ felicia community 

## +++ Romeo (unstable) +++
# deb http://packages.linuxmint.com/ felicia romeo 

## +++ Source Repositories +++
# deb-src http://packages.linuxmint.com/ felicia main upstream import 
# deb-src http://packages.linuxmint.com/ felicia community 
# deb-src http://packages.linuxmint.com/ felicia backport 
# deb-src http://packages.linuxmint.com/ felicia romeo 

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 8.10 Intrepid (stable) +++
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse 

## +++ Backports & Proposed (not as stable) +++
# deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse 
# deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted universe multiverse 

## +++ Source Repositories +++
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted universe multiverse 


## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu/ intrepid partner 

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ intrepid free non-free 


```

---

### Post by Silare Alvreon VI on 2008-12-02
Actually, so do I. Except I have Mint Elyssa x64 with updated repositories to fit Felicia.

You want to enable the last two Ubuntu repositories left by removing the # in front of them. The Amarok 2.0 package is in one of those repositories.

---

### Post by adobrakic on 2008-12-02
alright man, thanks a lot

---

### Post by Silare Alvreon VI on 2008-12-02
Glad to hear it worked. ^_^

---

### Post by adobrakic on 2008-12-02
i uncommented those two, and its showing that I have 77 updates now. I'm kind of afraid to do the whole update, because i really dont want that many unstable programs.

is there a way to just update amarok?

---

### Post by Silare Alvreon VI on 2008-12-02
Oh yeah, easily. Just search for the "amarok" package, and then click on the box to the left of the name, and say that you want to upgrade that package. It may upgrade a slew of other packages with it, but they're dependencies that Amarok 2.0 will need to have.

---

### Post by adobrakic on 2008-12-02
oh duh, forgot about doing it through synaptic
terminal spoiled me :x
thanks again man

---

### Post by Silare Alvreon VI on 2008-12-02
XD Ahh.

Well, in Terminal, this works too:

sudo apt-get update
sudo apt-get install amarok

Update would make all your packages adjust to the new repos that you enabled, and then you could install just Amarok (and it'll alert you of dependencies if you need it).

Glad it worked though, man. ^_^

---

### Post by terrordrone on 2008-12-14
```

# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://apt.wicd.net intrepid extras

```

That was my sources.list ..  i also have medibuntu repository
i am not getting upgrade to amarok2 ( i am on kubuntu 8.10 )

---

### Post by Skripka on 2008-12-14
> **terrordrone said:**
> 

That was my sources.list ..  i also have medibuntu repository
i am not getting upgrade to amarok2 ( i am on kubuntu 8.10 )

Here ya go:

[http://www.kubuntu.org/news/amarok-2.0](http://www.kubuntu.org/news/amarok-2.0)

---

### Post by adobrakic on 2008-12-14
Yeah, this never works for me either. I always end up getting Amarok 1.4.
Google Amarok-Nightly, they created an easy install for it. However, its not the final release, its beta 2.

---

