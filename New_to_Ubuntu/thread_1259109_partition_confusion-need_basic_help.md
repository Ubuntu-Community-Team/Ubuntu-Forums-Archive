---
title: "partition confusion-need basic help"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by relay_man on 2009-09-05
Listed below is the output of command:  fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00057278

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris
mike@mike-desktop:~$ 


I've googled and searched these forums without much luck,  So here goes.
I'm trying to learn linux starting with the basics of how the hdd is set up in a typical install.  This is my everyday machine I installed Intrepid on about 6-8 months ago and it runs just great.  I installed just accepting the defaults or suggested settings because I didn't/don't know anything about Ubuntu/Linux and I figured the defaults were best to get started.
I've read that linux needs at least two partitions, boot and swap.
From the above, I think my boot partition is sda/1.
I think the swap partition is sda/5.
I have no idea at all what sda/2 is...

My questions are:
1. Is sda/1 my boot partition, and if so why is it so big?

2. If sda/5 is my swap partition, I'd like it to be twice the size of
   my physical ram (8GB) but I'm not sure how big a "block" is.  Are
   blocks actually bytes?

3.  Why do sda/2 and sda/5 start and stop on the same cylinders?

4. I realise that hindsight is 20/20, but should I have manually
   set up the boot partition with approx. 20GB, the swap about 16 GB,
   and the rest of the disk a home partition? 

Because things have been working quite well and I've had really good luck with Intrepid, I'd like to stick with it.  Is it time to re-install from the same disc I originally installed from, but with better choices for number of partions and sizes?

Please Note:  If you are about to respond to any of the above by telling me how big an idiot or jackass you think I am, save yourself the trouble...
my wife beat you to that this morning at 6:00 a.m.


Any help would greatly appreciated

---

### Post by theozzlives on 2009-09-05
You're NOT an idiot! Root (/) should be about 10 - 20 GB, mine is 10, You don't need that much swap or re-install.

Start here: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/"). You'll need to resize SDA1 and SDA2. Make SDA2 8 GB (Same with SDA5). You'll need Partition Editor off your live CD. Create a new partition taking the rest of the free space, this will be your new /home.

SDA2 (extended) will always start at the same place as your logical (swap). After resizing and creating, you can then follow the instructions in the above link.

Good luck to ya!

---

### Post by Paqman on 2009-09-05
> **relay_man said:**
> 
My questions are:
1. Is sda/1 my boot partition, and if so why is it so big?


Nope, it's your root partition, or / for short.

That's the only one you *need*, although you'll almost always see a swap partition on a Linux system too.

Your root partition needs to be at least about 10GB, plus room for your data, installed programs, etc.

> 
2. If sda/5 is my swap partition, I'd like it to be twice the size of
   my physical ram (8GB) but I'm not sure how big a "block" is.  Are
   blocks actually bytes?


It won't need to be that big. If you have more than about 2GB of RAM, you're highly unlikely to ever use any swap at all. If you intend to use hibernation, then your swap must be at least equal to your RAM (as the contents of RAM get stored in swap during hibernation). Otherwise I wouldn't bother making it any bigger than 1GB. 8GB of RAM is more than your machine will ever be able to fill, so it just won't need to use swap space.

> 
3.  Why do sda/2 and sda/5 start and stop on the same cylinders?


Sda2 isn't really a real partition. It's an extended partition. It's just used as a container that you can create other partitions inside (such as sda5). The reason for this is that normally you can only have 4 partitions on a drive, but if one is an extended partition, then that can contain many more than that. So it's a useful thing to have.

> 
4. I realise that hindsight is 20/20, but should I have manually
   set up the boot partition with approx. 20GB, the swap about 16 GB,
   and the rest of the disk a home partition? 


Waaaaaaay too much swap, but otherwise a sensible setup, yes.

---

### Post by JC Cheloven on 2009-09-05
Just for your records:
-A single HD can have only 4 primary partitions.
-Nevertheless, that limit can be overcome by creating a 'extended' partition, which can stay along with a maximum of 3 other primary partitions.
-The extended partition is much as a box-for-partitions. There may be an unlimited number of partitions inside an extended one. The partitions inside an extended one, are 'logical' partitions.
-Linux works equally well on a primary or logical partition.
-Logical partitions start counting from 5, no matter if the possible primary partitions 1 to 4 are defined or not.

--> In your case sda1=primary. sda2=extended. sda5=logical.

-You only need so much swap if you plan to hibernate. Otherwise it is a waste of disk space.
-If you have enough ram, say 1Gb or more, it is advisable but not mandatory to have any swap. For example, it is better avoid it if your disk is solid state. 
-It is not mandatory to have a separate /home partition. Many people don't like it, and finds more handy to stick with the default setup, or to have a separate partition where to store their data (and eventually access it from two or more operating systems).

---

### Post by relay_man on 2009-09-06
Thanks everybody!

After some more research and checking out the link given, I think I'm getting it.:)
Once again, thanks for the input.

---

