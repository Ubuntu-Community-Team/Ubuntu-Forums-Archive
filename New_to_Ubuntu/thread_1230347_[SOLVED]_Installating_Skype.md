---
title: "[SOLVED] Installating Skype"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by nns2006 on 2009-08-03
Hi,
I am not able to install Skype. I have tried it by adding repository which says that failed to fetch all the packages information when i reloaded the package information.I have added that screen shot as attachments.
My problem does not ends here:( . I have tried to install Skype from Medibuntu not just one version i tried with every one static,OSS,etc... Here it says [COLOR="Red"]Error:wrong architecture 'i386[/COLOR]'. 
Any suggestions for me.
Thank you

---

### Post by LowSky on 2009-08-03
can you post the contents of this file
```
sudo gedit /etc/apt/sources.list
```

or try using the deb, directly

install this first 
[http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb)

then pick the one you need
32bit version
[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb)

64bit version
[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_amd64.deb)

---

### Post by K.L. on 2009-08-03
Try this. Download Static OSS Skype version and install 32 bit libraries by typing this in terminal:

```
sudo apt-get install ia32-libs
```
[]("http://www.skype.com/go/getskype-linux-oss")

---

### Post by nns2006 on 2009-08-03
> **LowSky said:**
> can you post the contents of this file
```
sudo gedit /etc/apt/sources.list
```

or try using the deb, directly

install this first 
[http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb)

then pick the one you need
32bit version
[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb)

64bit version
[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_amd64.deb)


# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by nns2006 on 2009-08-03
> **LowSky said:**
> can you post the contents of this file
```
sudo gedit /etc/apt/sources.list
```

or try using the deb, directly

install this first 
[http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb)

then pick the one you need
32bit version
[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb)

64bit version
[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_amd64.deb)

when i am trying to install 32 bit it says [COLOR="Red"]Error:Wrong architecture 'i386'[/COLOR] while installing with 64 bit it says [COLOR="Red"]Error: Breaks exisiting package 'skype' conflict: skype ( )[/COLOR]
what to do now?

---

### Post by nns2006 on 2009-08-03
> **K.L. said:**
> Try this. Download Static OSS Skype version and install 32 bit libraries by typing this in terminal:

```
sudo apt-get install ia32-libs
```
[]("http://www.skype.com/go/getskype-linux-oss")


still it gives the same Error: wrong architecture 'i386' :(

---

### Post by LowSky on 2009-08-03
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

remove that line from your source.list i think it is screwing things up

add the medibuntu repos using this commands

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

then run 

```
sudo apt-get update && sudo apt-get upgrade
```


then ```
sudo apt-get install skype
```

---

### Post by nns2006 on 2009-08-03
> **LowSky said:**
> ```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

remove that line from your source.list i think it is screwing things up

add the medibuntu repos using this commands

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

then run 

```
sudo apt-get update && sudo apt-get upgrade
```

then ```
sudo apt-get install skype
```




Hurrey!!!!!:popcorn:\\:D/=D>:grin:
Finally i can see that blue color(Skype). Thank you LowSky . I am able to install Skype.

---

### Post by LowSky on 2009-08-03
good to hear, and your welcome

---

### Post by aysiu on 2009-08-03
You should get into the habit of using *gksudo* with graphical applications.

It doesn't make that much of a difference for Gedit, but it does make a huge difference for other applications.

**Correct**: ```
gksudo gedit
``` **Incorrect**: ```
sudo gedit
``` It's a lot easier to just be in the habit of doing it the correct way instead of trying to keep a list in your head of what the applications are that it's okay to use the incorrect form with and which applications it's not okay to use the incorrect form with.

---

