---
title: "Installing Ubuntu 9.04 with XP using two HDDISK"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by HANZ99 on 2009-07-04
I have and XP system with two hard disk (200gb (C:) and 100gb(D:).
 
I want to install Ubuntu 9.04 in the 100GB (D:).
 
I tried to use 'advaance partition .. ' but no luck.
 
Is there info info has how to do two drives??
 
 
Hanz

---

### Post by diablo75 on 2009-07-05
Do you currently have anything stored on the 100GB drive?

---

### Post by philcamlin on 2009-07-05
click install over full hdd 

then it will work:popcorn::popcorn:

---

### Post by Jazzy_Jeff on 2009-07-05
Just boot into the live cd and then choose install. Make sure you choose the correct hard drive and tell it to use the whole thing.

---

### Post by presence1960 on 2009-07-05
**_First back up any data on the 100 GB disk!_** If you want to give Ubuntu the whole disk you can choose "Use entire disk" from the Prepare disk space window of the installer. Just switch the order of your hard disk in BIOS so the 100 GB boots before the windows disk. If you want a separate /home partition you will want to use gparted from the Ubuntu live CD or gparted Live CD to create a Ubuntu (/ or root) partition, swap partition and /home partition. I would recommend 15 GB for root (/), swap equal to your installed RAM and the rest for /home. if you go this route after creating the partitions install from the Live CD and choose "Manual" option at the Prepare disk space of the installer. You will then have to choose Filesystem type (ext 3 or ext 4) and mountpoint ( root is /. home is /home) for each partition. set swap as swap. Here is a screen shot of that Prepare disk space window of the Ubuntu installer as well as a link to download gparted Live CD. I prefer the gparted Live CD because you get the most recent version of gparted unlike the Ubuntu Live CD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by diablo75 on 2009-07-05
> **philcamlin said:**
> click install over full hdd 

then it will work:popcorn::popcorn:

Heh heh, whatever you do, make sure you don't do the above-quoted on the 200GB drive or you're Windows install will be royally screwed.

---

### Post by overdrank on 2009-07-05
> **philcamlin said:**
> click install over full hdd 

then it will work:popcorn::popcorn:

heh[-X

---

