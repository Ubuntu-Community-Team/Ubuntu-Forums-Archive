---
title: "Can I install specific applications from Live CD (Ubuntu already installed)"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-02-12
In another thread I ran into grub error 17 problems after using a windows-based programme to do partitioning work. It wasn't until I ran the Live CD while I was working through this problem that I realised that GParted existed.

I know I can install Gparted from 'add/remove applications' off the interwebs. Given it's somewhere on the Live CD as well, how I can install from it?

---

### Post by oldsoundguy on 2009-02-12
My experiences have show that you use gparted from the disk when you want to partition or re-partition a drive .. the install is done by re-booting the disk and starting from the install page.

If you are going to use the whole drive .. not needed to use gparted .. that is usually used when you want to create a dual boot system.  Something I have never done as I prefer separate os's on separate computers and use a KVM set up to switch between them.

---

### Post by mkvnmtr on 2009-02-12
I always install Gparted when I do a system but it only takes about two minutes to install from the package manager. You realize that if it is installed on your system you can't work on your system with it. You can only work on an unmounted partition and if you unmount the partition yuoour system is on you can't use the software on the system. You have to work on your partition from the live disk. I do use it quite often to work on external drives.

---

### Post by paulchinnz on 2009-02-13
Thanks for the advice about using gparted. 

What I'm after though is how to install gparted off the Live CD (or if it's possible).

---

### Post by hellion0 on 2009-02-13
Run Synaptic. Put the CD-ROM in the drive. It should read it as a source. If it doesn't right away, you may have to open Settings -> Repositories in Synaptic. From there, search for 'gparted.' If it's on the disc, you can install.

**However**, you should be very aware that you cannot use GParted on the same drive it's running on, even a different partition on that same drive! This is why it's present on the LiveCD but not installed - many systems are single-drive and thus don't have any use for installed GParted.

---

### Post by geirha on 2009-02-13
I'm afraid the liveCD contains very few packages, simply because there's no room for all those packages and the live session at the same time. The installer actually copies the files needed from the live session, rather than installing packages. The alternate CD, which just has a small text installer, contain all packages needed for a fresh install, but gparted is not included on that one either. You'll need to get hold of a dvd-image ([http://cdimage.ubuntu.com](http://cdimage.ubuntu.com)) or have synaptic create a download script for gparted if you want to have it installed without a network connection.

---

