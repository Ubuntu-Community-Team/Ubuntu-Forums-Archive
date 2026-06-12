---
title: "Downloading Current Kernel Sources"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-01-15
So to resolve the issue with my G1Sn I need to download the Kernel sources add a few lines and then recompile and install the new files. I found the following lines that are suppose to do it on nVidia's forums: ```
# Install Kernel Sources
sudo apt-get build-dep linux-image-2.6.24-17-rt
sudo apt-get source linux-image-2.6.24-17-rt

# Install Kernel Modules Sources
sudo apt-get build-dep linux-ubuntu-modules-2.6.24-17-rt
sudo apt-get source linux-ubuntu-modules-2.6.24-17-rt

# Apply NVRM patch (download the patch first!)
sudo patch -p0 < NVRM_512M_fix.txt

# Build debs for linux-image & linux-headers
cd linux-2.6.24/
sudo cp /boot/config-2.6.24-17-rt debian/config/amd64/config.rt
sudo CONCURRENCY_LEVEL=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-rt
cd ..

# Build Kernel Modules
cd linux-ubuntu-modules-2.6.24-2.6.24/
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules binary-debs
cd ..
```

Here is the code for the patch that was given: ```
diff -Naur linux-2.6.24.orig/arch/x86/pci/i386.c linux-2.6.24/arch/x86/pci/i386.c
--- linux-2.6.24.orig/arch/x86/pci/i386.c	2008-06-03 20:24:26.000000000 -0400
+++ linux-2.6.24/arch/x86/pci/i386.c	2008-06-03 20:25:40.000000000 -0400
@@ -122,6 +122,10 @@
 				r = &dev->resource[idx];
 				if (!r->flags)
 					continue;
+				if ((r->start == 0xbdf00000) && (r->end == 0xddefffff)) {
+					r->start = 0xc0000000;
+					r->end = 0xd0000000;
+				}
 				pr = pci_find_parent_resource(dev, r);
 				if (!r->start || !pr ||
 				    request_resource(pr, r) < 0) {
```

How ever running the above posted code tells me it cannot find the package I am looking for when I run the first line, I also tried updating the versions to the current Kernel version but that still did not work either. This is the original thread on the NVNEWs boards: [http://www.nvnews.net/vbulletin/showthread.php?p=1673409#post1673409](http://www.nvnews.net/vbulletin/showthread.php?p=1673409#post1673409)

I tried posting there but it seems like the thread is long dead... anyone here have any ideas how I can download the needed files and maybe how I add these lines to it?

Help Please!
~Jeff

---

### Post by zvacet on 2009-01-16
In your source list you needto add src repos or if you allready have them remove # sign in front of them.I believe that you are runing Gutsy so look [here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories") how repos look like.Same thing if I'm wrong about version.Run in terminal

```
gksudo gedit/etc/apt/sources.list
```

and then make changes.Save and close file.

```
sudo apt-get update
```

---

### Post by beastrace91 on 2009-01-16
I am running 8.10, how ever I do not see and "src repos" commented out in my sources.list.

Maybe I am missing it though... Here is my sources.list ```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

``` What are the lines I should add to get the repos I need working? I really want to get my extra ram installed...

~Jeff

---

### Post by bwang on 2009-01-16
When you try to install the packages what errors does apt-get give you?

---

### Post by beastrace91 on 2009-01-17
Gah I feel slightly stupid, I had a typo when I was editing the kernel version...
```

sudo apt-get build-dep linux-image-2.6.27-9-generic
``` Worked... it is downloading now... hopefully I can figure this out and get it all working swiftly.

~Jeff

---

### Post by beastrace91 on 2009-01-17
Ok so I got the kernel sources using the following:

```
# Install Kernel Sources
sudo apt-get build-dep linux-image-2.6.27.9-generic
sudo apt-get source linux-image-2.6.27.9-generic

```

How ever when I get to this next part: ```
# Install Kernel Modules Sources
sudo apt-get build-dep linux-ubuntu-modules-2.6.27.9-generic
sudo apt-get source linux-ubuntu-modules-2.6.27.9-generic

```

I get ```
jeff@jeff-ubuntu:~/Kernal$ sudo apt-get build-dep linux-ubuntu-modules-2.6.27.9-generic
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for linux-ubuntu-modules-2.6.27.9-generic

```

Anyone any ideas what the Kernel Module Source packages are called?... This guide I am trying to follow is obviously dated but it is the only solid lead I have been able to find towards making my ram work...

~Jeff

---

