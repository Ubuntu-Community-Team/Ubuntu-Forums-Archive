---
title: "cannot upgrade packages"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Matt26 on 2009-04-29
i'm not able to upgrade a couple of packages via update manager- they are grayed out and after trying to upgrade one of them (kdekibs5) via synaptic package manger i get the error message i have attached- one of the dependencies listed (kdelibs-bin) is the other grayed out item in the update manager.

i have tried reinstalling the other packages that the error message message lists but i still can't upgrade these two particular packages.

does anyone know how i can fix/upgrade these packages?

thanks.

---

### Post by taurus on 2009-04-29
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Duskao on 2009-04-29
There are probably some dependency issues. I had the same problem with one of my programs after upgrade. I found this out with add/remove and tried to remove it and it said that there was a dependency on another program and it referred me to synaptic package manager. I then removed the program that it had a dependency on and it worked for me. Careful of what you might be trying to remove through the synaptic package manager because if you remove the wrong things I'm sure you could mess up your system.

---

### Post by Matt26 on 2009-04-29
> **taurus said:**
> Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

---

### Post by taurus on 2009-04-29
What if you edit /etc/apt/sources.list and place a # in front of the last line to comment it out.

```
**[COLOR="Blue"]#[/COLOR]**deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by donaldt on 2009-04-29
OK, here is my story.  I have been avoiding any upgrades from 8.10 to 9.04 because I was afraid of corrupting my newly configured NVIDIA X server driver.  I had a terrible time getting one installed, could not initially get it working on my second display, etc.  After achieving some success, I didn't want to take a chance on anything new.  I'd have to re-jigger the kernel, no thanks.  Didn't want any of that right now.

So, I fire up Ubuntu today and there are new downloads available.  Not being very observant, I hit install.  OH MY G__  Look what's happening!  It's downloading and installing 9.04!  Crap, too late to change now, it would mess up the process.  

So I sit and watch this show/process for about an hour.  Imagine my surprise when the screen resolution improves, the NVIDIA driver is configured and the kernel upgraded, all without any action on my part.  The screen looks great and the whole process was done with no action on my part.

I LOVE UBUNTU!!

Donaldt

---

### Post by Matt26 on 2009-04-29
> **taurus said:**
> What if you edit /etc/apt/sources.list and place a # in front of the last line to comment it out.

```
**[COLOR="Blue"]#[/COLOR]**deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

yes, that got rid of the grayed out items in the update manager- but correct me if i'm wrong here- doesn't that just prevent that particular source from being checked for upgrades- so if there are any upgrades available (like in my case) then they just wouldn't show up?

i'm guessing if i remove the # from that line the package upgrades will show up in update manager again.

if that's the case then this really doesn't resolve the issue with the upgrades not being able to be installed- it just 'ignores' them so they don't show up.

thanks for your suggestion.

---

