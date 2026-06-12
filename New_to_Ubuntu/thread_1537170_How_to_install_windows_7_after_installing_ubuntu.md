---
title: "How to install windows 7 after installing ubuntu"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by ventehxieteh on 2010-07-23
the situation is, I fully installed Ubuntu 10.04 on my 160gb hard drive meaning no partition whatsoever. I want to dual boot windows 7 is there a way? I tried to look for the answer here and else where but all i get is that you must install windows 7 first or partitioned the drive even before Ubuntu installs..

is it possible?

sorry if this has been asked before but I can't find the answer

---

### Post by M1ke on 2010-07-23
> **ventehxieteh said:**
> the situation is, I fully installed Ubuntu 10.04 on my 160gb hard drive meaning no partition whatsoever. I want to dual boot windows 7 is there a way? I tried to look for the answer here and else where but all i get is that you must install windows 7 first or partitioned the drive even before Ubuntu installs..
 
is it possible?
 
sorry if this has been asked before but I can't find the answer
 
I'd take the commonly-given advice that you've already come across in that case; apparently the simplest way is for Windows to be installed first.
 
If you're concerned because you've already got Ubuntu set up just the way you like it, maybe you'd be encouraged by the fact that transferring all your settings and customisations to a fresh installation is really quick and easy? If you backup all the hidden folders in your /home folder and put them back there on the new installation, your apps will retain all their settings when you install them again.

---

### Post by ventehxieteh on 2010-07-23
well i thought of that but problem is.. i dont have any external hard drive.. well no choice i guess thanks for the answer

---

### Post by Locke_99GS on 2010-07-23
Use gparted (or other) to make room for Windows. Install Windows 7 onto the new partition, then boot a LiveCD and fix grub.

---

### Post by redbook4574 on 2010-07-23
My favoured method is to install windows to a new partition, then boot from a live copy of super grub to your ubuntu partition,

once in ubuntu from terminal run sudo grub-install /dev/sda

This should restore your grub boot loader.

you should also be able to run this from a live version of ubuntu.

---

### Post by ventehxieteh on 2010-07-23
> **Locke_99GS said:**
> Use gparted (or other) to make room for Windows. Install Windows 7 onto the new partition, then boot a LiveCD and fix grub.

can you give me a guide how to do that exactly cause i can't.. gparted doesn't allow me to mess with my ubuntu partition

---

### Post by ronnielsen1 on 2010-07-23
I've installed Windows 7 after the fact. You will have to partition and I would recommend having the space for Windows at the front which will take some time using gparted to move the files in Ubuntu. You would also have to reinstall grub2

> **Installing Windows After Ubuntu**

 Normally when Windows is  installed after Ubuntu the "Master Boot Record", MBR, will be  overwritten. You can bootup off a [LiveCD]("https://help.ubuntu.com/community/LiveCD") and repair  the MBR. However, there are 2 different approaches: 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 > **SIMPLEST - Copy  GRUB 2 Files from the LiveCD**

 This is a quick and simple  method of restoring a broken system's GRUB 2 files. The terminal is used  for entering commands and the user must know the device name/partition  of the installed system (sda1, sdb5, etc). The problem partition is  located and mounted from the LiveCD. The files are then copied from the  LiveCD libraries to the proper locations and MBR. It requires the least  steps and fewer command line entries than the following methods. 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
> **“How to” Dual boot Ubuntu and Windows 7 (Ubuntu installed first)**
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by Mark Phelps on 2010-07-23
> **ventehxieteh said:**
> can you give me a guide how to do that exactly cause i can't.. gparted doesn't allow me to mess with my ubuntu partition

You can't mess with a partition while it is in use; so, you can't use GParted from within Ubuntu on its own  partition.  You have to boot from a LiveCD and do it that way.

Also, make sure that the partition you are resizing is not mounted.  You can see that in the dialogue box by looking to see if there is a mount point shown for the partition.  If there is, use the menu and unmount it.

Also, GParted tends to be very s...l...o...w, so don't get impatient and end it early or turn your machine off.  It does the major operations twice -- so it takes a long time.

---

### Post by ronnielsen1 on 2010-07-23
> You can't mess with a partition while it is in use; so, you can't use  GParted from within Ubuntu on its own  partition.  You have to boot from  a LiveCD and do it that way.
Forgot that step

---

### Post by ventehxieteh on 2010-07-23
after extensive research.. i figured out what to do thanks for your suggestions..

what i did was i used a live ubuntu to partition my hardrive giving space for windows..
i will install windows 7 after reformatting the unallocated space to ntfs then recover grub..

i gave my windows 7 40 gb then 100+ to ubuntu since i will use it more maybe i should have given windows less.. but you never know when you'll need more

---

