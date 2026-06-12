---
title: "USB Persistent install issues"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by tonifiddle on 2009-09-15
Hallo to every one here in Ubuntu Forums.This is my very first post and I'm happy to be part of the World's biggest Linux forum.
  
Here is my problem.
I did  install of Ubuntu 9.04 on my USB thumb-drive with persistent mode ON (I've created myself casper-rw file with custom size so it can fit well for my needs).
It runs well with no issues except for one.
When i try to re-partition my hard drive I cannot do it because one or more partitions are mounted and cannot unmount them with any force or command. 
I've been trying every possible command in Terminal but it did not work. 
Mount point "cdrom" cannot be released.My NTFS and/or FAT32 partitions are blocked(mounted) and I cannot perform any modification - delete,resize or format

Those partitions are automatically mounted at startup and cannot be unmounted.
Is there a work around to solve this small problem.Otherwise it is almost useless for my needs.I want to be able to reformat partitions and to install Ubuntu directly from the USB thumb-drive  

Thanks Tony :guitar:

---

### Post by zeroseven0183 on 2009-09-15
I haven't done this repartitioning of USB drive where Ubuntu is installed but I can only think of one thing, boot from LiveCD with the USB inserted.

---

### Post by mantelo on 2009-09-17
You are going to need to boot from a cd or a different pen drive in order to do the partitioning. Once you reformat tha hard drive, boot your persistent install back.

---

### Post by LewRockwell on 2009-09-17
we are assuming you've turned your swap off```
sudo swapoff /dev/*your swap drive/partition here*
```and dismounted the internal hard drive```
sudo umount /dev/*your hard drive here*
```.

---

