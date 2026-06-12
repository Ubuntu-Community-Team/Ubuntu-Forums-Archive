---
title: "File discrepancy, et al"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by robertlow on 2010-02-22
I'm transitioning my machines to Linux.

Two questions:
1) The latest install was difficult because my old machine choked on the restricted nvidia driver. It's now up, but the download software option brings up the menus, then finds nothing to download. I suspect a package failed to install. Perhaps someone could shed some light on this, because I need a copy of Gnome Partition Editor to clean up the old disks I installed.

2) In comparing the contents of Var/cache/apt/archives, I discovered a file called:

fakeroot_1.12.4ubuntu1_i386.deb

This file exists on the machine imaged a couple of weeks ago, but not on the newer install to the rebuilt machine. The 4ubuntu1 part sounds like it has something to do with Ubuntu One, but the fakeroot part doesn't sound too good.

I'm absolutely new to linux, and haven't found the wedge I need to open it yet. Steep learning curve. However thanks to a lot of knowledgeable people, I've been able to find enough information to limp into something like productivity. My very sincere thanks to the wonderful organization you have built.

Robert Low

All questions answered. Thanks, Ann!
(Actually I searched for and downloaded gparted through synaptic package manager just before checking in with the forum.)
Copied the command line, though.
A lot to learn, but I'm workin' on it. Thanks again.

---

### Post by oldos2er on 2010-02-22
fakeroot is an Ubuntu package; here's its description: This package is intended to enable something like:
   dpkg-buildpackage -rfakeroot
 i.e. to remove the need to become root for a package build.
 This is done by setting LD_PRELOAD to libfakeroot.so,
 which provides wrappers around getuid, chown, chmod, mknod,
 stat, and so on, thereby creating a fake root environment.

To install gparted, use ```
sudo apt-get update && sudo apt-get install gparted
``` in a terminal. If it fails for some reason, please copy and paste the output here.

---

