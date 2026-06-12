---
title: "Partitioning the Hard Drive"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Steelfan555 on 2009-06-02
I was running Ubuntu under Wubi/XP. Recently i have upgraded to Win7, and now im missing Ubuntu! I'd rather not use Wubi this time, so i went to partition my hard drive. I found out i have 5 partitions, and thus i am not able to create any more. I was wondering if there was a way to get rid of all of the partitions other then the c drive, then i can partition a piece for Linux.
Also, im downloading 9.04 and will be installing that.
-Steel

---

### Post by aktiwers on 2009-06-02
Do you have data on those partitions you want to keep?
If not you could just delete them and create a simple setup:

One Partition on about 1gb with filesystem SWAP
And one with the rest of the free space, Filesystem EXT4 and in mountpoint write ```
/
```

But remember, deleting the partitions will loose the data on them !

---

### Post by Steelfan555 on 2009-06-02
Ok, i deleted every partition but 2 (Win7 and backup (.1gig). should i give the rest to c/ (windows) and format it while installing ubuntu, or should i create a separate partition in windows?

---

### Post by goxi on 2009-06-02
> **Steelfan555 said:**
> I was running Ubuntu under Wubi/XP. Recently i have upgraded to Win7, and now im missing Ubuntu! I'd rather not use Wubi this time, so i went to partition my hard drive. I found out i have 5 partitions, and thus i am not able to create any more. I was wondering if there was a way to get rid of all of the partitions other then the c drive, then i can partition a piece for Linux.
Also, im downloading 9.04 and will be installing that.
-Steel
I`m using winXP and Ubuntu 9.04. Previousli I used several other linux distros on same partitions I made for this purpose. 
First I made 2 partitions (C and D) during installing winXP. After that, with PARTITION MAGIC i resized partition D and made two new partitions with 10GB and 512MB. After that with same program I formated them to ext2 filesystem and Linux SWAP.
Second I inserted Ubuntu / Fedora / Knoppix / DSL ... or any other distro and using install procedure or FDISK , I formatted this partitions i needed filesystem and after that I installed linux distros on it.
Wuth Ubuntu 9.04, all you need to do is to create partitions with above program and to follow install procedure on ubunti CD (od DVD).
GOOD LUCK !!! ;)

---

### Post by aktiwers on 2009-06-02
Oh so you are doing a clean install of Windows as well..

I usually just pick during the Windows installation how much space to use on XP, say 15-25gb.. Then use the rest for Ubuntu.

Remember to Install Windows first and then Ubuntu, because if you do it the other way around, Windows installer will kill your bootloader.

---

### Post by bodhi.zazen on 2009-06-02
Here is an overview of partitioning :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

You can only have 4 primary partitions. You can have many many more logical partitions in an extended partition, you have to make space.

Use gparted from a live CD to make space.

---

### Post by Steelfan555 on 2009-06-02
Any reason i cant use the built in partitioner? And do i need a swap?

---

### Post by lisati on 2009-06-02
> **Steelfan555 said:**
> Any reason i cant use the built in partitioner? And do i need a swap?

The one and only time I've tried to use the Vista partitioner it didn't let me, possibly because I was trying to tinker with the Vista partition at the time. I ended up using gparted on a Live CD. 

Depending on your system specs you *might* be able to get away with not having a swap partition. There are a few things to keep in mind, like whether or not you want to use things like suspsend/hibernate, and what sort of performance you'd like from your system.

---

### Post by Steelfan555 on 2009-06-02
Ok, thanks for the help. Gparted is burning right now and 9.04 is downloading as well. The Windows partitioner only supports NTFS and FAT32, so thats not nice. Ill post the end results. 

**Also, ext2, 3 or 4?**

---

### Post by lisati on 2009-06-02
p.s. As I understand it, one of the historical reasons for including a swap partition is to help with system performance.

---

### Post by aktiwers on 2009-06-02
SWAP is like the pagefile in windows, that means the system can write to that space instead of to RAM if needed. I have 4gb RAM and 1 gb Swap and I really never use my Swap space, but I keep there anyways for some reason..

---

### Post by bodhi.zazen on 2009-06-02
> **Steelfan555 said:**
> Ok, thanks for the help. Gparted is burning right now and 9.04 is downloading as well. The Windows partitioner only supports NTFS and FAT32, so thats not nice. Ill post the end results. 

**Also, ext2, 3 or 4?**

Gparted is included on the Ubuntu Live CD , so no need to DL / Burn the gparted live CD (although It is a nice tool).

ext3 is probably best.

---

### Post by Steelfan555 on 2009-06-04
Thanks. I had a copy i used for other things too, but lost it. Everything worked fine, used ext3. 
9.04 rocks, first time my wifi worked after installing the restricted driver!

---

