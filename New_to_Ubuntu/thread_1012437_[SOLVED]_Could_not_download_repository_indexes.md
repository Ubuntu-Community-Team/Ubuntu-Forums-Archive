---
title: "[SOLVED] Could not download repository indexes"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by captgadget on 2008-12-15
Here is a screen shot and I've checked the sources.list but don't find any of these in there. Anyone know how I can correct this? I also don't see them in the Software Sources.

---

### Post by taurus on 2008-12-15
Are you behind a proxy or did you somehow install something similar to anon-proxy thing?

Otherwise, post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by captgadget on 2008-12-15
Here's my sources.list

---

### Post by oldos2er on 2008-12-15
Can you please copy & paste your sources.list here? Your screenshot doesn't show the whole file.

---

### Post by captgadget on 2008-12-15
let's try this.

---

### Post by captgadget on 2008-12-15
Well, here it is.
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/intrepid-proposed](http://archive.ubuntu.com/ubuntu/intrepid-proposed) main restricted universe multiverse

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid free non-free
deb-src [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid free non-free

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb [http://archive.canonical.com/](http://archive.canonical.com/) intrepid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) intrepid partner

---

### Post by maddog46113 on 2008-12-15
Try this
```
sudo apt-get clean
```
```
sudo apt-get update
```

I recently had a problem apt-get clean fixed it.

---

### Post by captgadget on 2008-12-15
this is what it returned:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/intrepid-proposed/dists/main/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/intrepid-proposed/dists/main/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/intrepid-proposed/dists/main/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/intrepid-proposed/dists/main/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/intrepid-proposed/dists/main/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/intrepid-proposed/dists/main/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by taurus on 2008-12-15
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of this line.

```

**[COLOR="Blue"]#[/COLOR]**deb http://archive.ubuntu.com/ubuntu/intrepid-proposed main restricted universe multiverse

```
Save it.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Tatty on 2008-12-15
It is only the intrepid-proposed updates which it is struggling with.  Do you mean to have this selected in your sources.list file?

For now turn it off via System->Administration->Software Sources->Updates.  Turn it back on if you have a reason to, otherwise they are only really intended for developers [https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

---

### Post by captgadget on 2008-12-15
I'm sure u r right, but by golly I keep looking and can't find 'em.

---

### Post by drs305 on 2008-12-15
The line 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)**/intrepid-proposed** main restricted universe multiverse

needs a space in it after the **ubuntu.com/ubuntu/**

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)**  intrepid-proposed** main restricted universe multiverse

---

### Post by captgadget on 2008-12-15
Found it!!!!!! Thanx for pointing it out.

---

### Post by taurus on 2008-12-15
> **drs305 said:**
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)** /intrepid-proposed** main restricted universe multiverse

I thought it should be

```

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)** intrepid-proposed** main restricted universe multiverse

```

---

### Post by drs305 on 2008-12-15
> **taurus said:**
> I thought it should be

```

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)** intrepid-proposed** main restricted universe multiverse

```

It certainly should. Typo corrected. I can't keep anything straight with all the formatting symbols!

---

### Post by captgadget on 2008-12-15
Hey!!! Thanx to everyone here who helped straighten this out.

---

### Post by taurus on 2008-12-15
> **drs305 said:**
> It certainly should. Typo corrected. I can't keep anything straight with all the formatting symbols!

Yeah, tell me about it.  One time I made a typo of using cd to a file (instead of more or vi/nano) and one guy jumped in and rolled his eyes at it.

---

