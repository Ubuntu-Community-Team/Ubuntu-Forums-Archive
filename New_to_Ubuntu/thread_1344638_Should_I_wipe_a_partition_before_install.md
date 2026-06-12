---
title: "Should I wipe a partition before install?"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-03
Hi do you think it is better to wipe clean my paritions before installing any new OS? I am actually referring to windows since I would like to dual boot Windows 7 + Ubuntu 

Thanks ;)

---

### Post by wilee-nilee on 2009-12-03
> **listerdl said:**
> Hi do you think it is better to wipe clean my paritions before installing any new OS? I am actually referring to windows since I would like to dual boot Windows 7 + Ubuntu 

Thanks ;)

It really doesn't matter you could do a wipe that wrote it to all 0's or delete. The main thing you want to do is when you install W7 use the custom install and have it write a partition to the size you want to dual boot then you don't have to shrink it, and you have an empty space for Ubuntu to custom partition or let the partition Gui do a auto.

If it was me I would just delete the partitions with the live CD then install W7 first. In order to delete with the live CD your have to turn swap off if you have Ubuntu installed now.

---

### Post by Astarroth on 2009-12-03
I agree..You will have less problems down the road if you wipe the partition and do a fresh install. That is what I did when I did my dual boot w7/9.10 setup.

---

### Post by listerdl on 2009-12-03
> **wilee-nilee said:**
> ...........If it was me I would just delete the partitions with the live CD then install W7 first. In order to delete with the live CD your have to turn swap off if you have Ubuntu installed now.

How do I do that? Is it straightforward to "delete the partitions with the live CD"

---

### Post by listerdl on 2009-12-03
> **Astarroth said:**
> I agree..You will have less problems down the road if you wipe the partition and do a fresh install. That is what I did when I did my dual boot w7/9.10 setup.

How do you wipe the partition?

---

### Post by szymon_g on 2009-12-03
the easiest way- its to format it in new filesystem (if you are planning to use old, un-used ntfs partition you will have to format it anyway)

---

### Post by Bartender on 2009-12-03
If you want a stand-alone partitioner follow the link under my sig to download an .iso of the GParted LiveCD.  It's essentially the same partitioner in the Ubuntu LiveCD but it's just the partitioner.
It seems to work better as a stand-alone partitioner, plus it's a great all-around tool for working on PC's.

---

### Post by listerdl on 2009-12-03
Bartender - Thanks for that ...what do you mean by a 'stand-alone partitioner'?

Also, is GPartedLiveCD easy to use or do I need to understand partions as an expert before using?

---

### Post by cartisdm on 2009-12-03
> **listerdl said:**
> Bartender - Thanks for that ...what do you mean by a 'stand-alone partitioner'?

Also, is GPartedLiveCD easy to use or do I need to understand partions as an expert before using?

I have always been a big believer in using GParted to wipe the drive before I go installing a new OS but lately I've been lazy and just used the "Advanced" section of disk management in the Windows 7 (and Vista) OS install wizard.  I haven't had any problems with any dual boot setups.

The link that Bartender will provide you with a file to download that you will turn into a bootable LiveCD (similar to ubuntu cds).  It's a stand alone partitioner because it allows you to boot into the CD instead of the HD, thus allowing you to make instant changes to all the drives.

[It's easy to use too!]("http://www.wikihow.com/Use-Gparted")

---

### Post by Bartender on 2009-12-03
> **cartisdm said:**
> The link that Bartender will provide you with a file to download that you will turn into a bootable LiveCD (similar to ubuntu cds).  It's a stand alone partitioner because it allows you to boot into the CD instead of the HD, thus allowing you to make instant changes to all the drives.

[It's easy to use too!]("http://www.wikihow.com/Use-Gparted")

+1 
By "stand-alone" I mean that's all that the GParted LiveCD (I call it GPLCD for short) does.  GPLCD looks the same as the partitioner you would see if you start up an Ubuntu LiveCD, choose "Run Ubuntu without making any changes", wait for the desktop, then go to Administration>Partitioner.
It looks the same because they're both gparted, an open source partitioner.
Maybe this is just me, but I find it appealing to have the partitioning tool on a separate CD that does nothing else but let you look at your discs and partition them if you want.
Rather than starting up Ubuntu, going to the desktop, etc. etc.

Also, the stand-alone GPLCD is a little smoother than the version of gparted on the Ubuntu disc.  For instance, you don't have to unmount swap if you want to move or delete it.

Here's a post of mine from a few months back with some discussion of GPLCD, some screenshots, etc.
  
[http://ubuntuforums.org/showthread.php?t=1249374](http://ubuntuforums.org/showthread.php?t=1249374)

Also check out the gparted website as mentioned by cartisdm.  Plenty of guides and screenshots.

I think GPLCD is easy and fun to use, but yeah it was a little confusing the first couple of times.  Half of that was unfamiliarity with the application, the other half was unfamiliarity with partitioning basics, like what's really the difference between extended and logical, etc.

What I really like about GPLCD is you can set things up beforehand just the way you want them.  Create a primary partition for Windows, format it to NTFS.  Create extended partition, then make your logicals inside.  Set up your swap partition.  There's been a few times where GPLCD really came thru for me, like when a Xubuntu LiveCD refused to recognize a partition until I went back to the GPLCD and formatted the partition as ext3.  Popped the Xubuntu disc back in and it went "Oh, OK, I know what to do with this" and we were off and running.

---

