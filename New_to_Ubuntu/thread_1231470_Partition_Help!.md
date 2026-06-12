---
title: "Partition Help!"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by dino1515 on 2009-08-04
I am fairly new to the Linux scene and I absolutely love Ubuntu!

I have attached a picture of the way my partitions are currently setup. I have a dual boot of Ubuntu and Vista. The fact is I do not understand it at all. All I understand is that ext3 is my ubuntu partition and ntfs is Vista. I wish to know what extended, linux swap and unallocated are. and also why there are two ntfs partitions.

I also wish to be able to make just two partitions if possible, one for vista and one for ubuntu, and I want ubuntu to be the larger. I have looked up lots of tutorials etc. but i have been unable to figure this out, also because I have no idea what any of the partitions on my computer are.

Any help would be appreciated especially if it is in simple form so I can understand!

---

### Post by howefield on 2009-08-04
> **dino1515 said:**
> I wish to know what extended, linux swap and unallocated are. and also why there are two ntfs partitions.

I'm guessing your second ntfs drive at the end of the disk is your recovery partition for your windows install, you probably do not want to remove it, at least without being clear of the consequences.

Your linux swap is the place that Ubuntu will use if it runs out of physical memory, something you probably want to keep.

The unallocated is simply that, a part of the disk unoccupied by anything, waste of space but it is only a couple of megabytes.

The extended partiton (containing ext3 Ubuntu and swap partitions) has been made by the Ubuntu install when it shrunk the windows partition to make room for Ubuntu. Had you used gparted to manually create the partitions prior to installing Ubuntu, you could have had four primary partitions on one disk, one for each of windows, ubuntu, swap and recovery partition.

---

### Post by bodhi.zazen on 2009-08-04
Some of your questions are answered here :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

For Ubuntu you need only one partition, / , or root. You should consider using a swap partition as well.

The size of your swap depends on how much RAM you are using and if you are using a laptop with suspend.

[Swap FAQ - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SwapFaq") 

I am mot sure I agree with everyting on that SWAP FAQ page, but it is a good place to start.

---

