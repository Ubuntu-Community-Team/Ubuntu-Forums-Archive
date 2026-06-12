---
title: "Vista-64, Ubuntu-64 Dual boot, Installation, Partitions"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by #include on 2009-04-03
Hi all,

I have been doing a ton of reading, and am looking to jump in to using Linux almost exclusively. For the occasional gaming reason, I will not be able to completely rid myself of Vista, but here is my plan - and I would like to bounce my ideas off the Ubuntu community.

My goal is to use Ubuntu as a springboard into learning and understanding Linux. At an indefinite point in the future, my goal is to run a very minimalistic distribution. Until that day comes, I will learn about the base OS using Ubuntu.

My computing needs are fairly complex. As of right now, I see myself using office tools, gaming, web design, high definition audio listening and video encoding. For the most part, it will be a media center (I prefer to just use the OS, not use a Linux equivalent to Windows Media Center).  

For security reasons, I would like to use True Crypt. I have 8GB of Corsair memory, so 32-bit OS builds are really not a good choice for me.

Possible future configurations include a RAID system, and complete media center integration.

OK - On to my questions.

How should I partition my hard drive?
- I have a 600GB HD
- I would like my audio to be accessible on both OS
- I would like each OS to have a basic "OSDisk" style install

I've read that I should install Vista before installing Ubuntu. With this OSDisk style partition, should I do say 20GB for Vista64, then format the remaining space? Then do an Ubuntu partition using a the OS size + 5-10GB of space? 

Would I wait to install True Crypt until after I have installed both OS?

My head is swimming. I will come back routinely throughout the day, and will be doing all of this fresh tonight.

---

### Post by jamesrfla on 2009-04-03
I am not sure about the true crypt. 20GB is a little to small for Vista 64bit. I would give it at least 40GB. It also depends what are you going to put on vista. After you install Vista what are you going to put on it? Also it would be easier to have the music on the Vista partition because if you put it on Ubuntu you would need a program to be able read the Ubuntu partition from Vista. You can also just create a 3rd (or 4th partition if you add SWAP, EXT3, and NTFS) and put all of your music on that.

---

### Post by #include on 2009-04-03
I would like both partitions to be as close to the OS only as possible. I would like to store all of my audio on a 3rd (or beyond) partition. The Vista partition would need to hold the drivers for all of my hardware, CS:S, and about an extra 15-20GB for any other games/apps I want in the future.

Would it be possible to use a 3rd or more partition to hold audio/movies, which could be read by both platforms?

---

### Post by ibuclaw on 2009-04-03
Given that you have 600GB of hard drive space, I would allow myself at least a bit more room to maneuver.

1) Yes, first you install Vista, due to the way it installs itself on the MBR.
Space-wise, I would say around 40GB should be sufficient.

2) Before installing Ubuntu, setup the partitions while in the Ubuntu LiveCD beforehand.
Just go to **System->Administration->Partition Manager** in the dropdown menu.

If you are just wishing to dual boot and nothing else, I suggest that you create 3 partitions after the Vista one.

[LIST]
[*] 1) **Ext3** Partition, 20GB. This will house the base install of Ubuntu.
[*] 2) **Swap** Partition, 1.5 times the amount of RAM you have (ie: if you have 1GB RAM, make 1.5GBs of swap).
A swap partition for Linux is what a paging file is for Windows.
[*] 3) **NTFS** Partition, to fill up the remaining 500GB space. NTFS is readable by both Linux and Windows, so long as you don't enable NTFS compression or encryption whilst in Windows Vista.
[/LIST]

Since implementing this will use up all Primary Partition slots on your hard drive, you may benefit from putting the 500GB NTFS partition on an Extended Partion, so you could shrink it and split it into many separate partitions at a later date if you choose to.

Regards
Iain

---

### Post by -kg- on 2009-04-03
> Since implementing this will use up all Primary Partition slots on your hard drive, you may benefit from putting the 500GB NTFS partition on an Extended Partion, so you could shrink it and split it into many separate partitions at a later date if you choose to.

In fact, upon installing Vista in it's 40 GB Primary partition, you could make the remaining space an Extended partition and create the other partitions as Logical partitions within it.  Ubuntu (Linux) will install into and run from a Logical partition, and Vista will access an ntfs Logical partition (and ext as well, if you install the proper driver software) just as well as a Primary one.

Do some reading on ["How To Partition"]("https://help.ubuntu.com/community/HowtoPartition") in the Community Documentation for more information.

> 1) Ext3 Partition, 20GB. This will house the base install of Ubuntu.

If you are not going to be creating a separate /home partition, I would suggest more than 20 GB on your size of hard drive.  I personally would give it, say, 50 GB, since in that configuration your /home directory will be on the / (root) partition.  Also, I would give myself more room just for experimentation purposes.  I have a root partition that is separate from my /home partition at 20 GB.  I have 4.8 GB free left, and I don't have all that much installed.  I do, however, have quite a bit of room in my /home partition.

These sizes depend on what you anticipate doing, making allowances for the unknown.  I would give it *plenty* of room (especially considering the size of your hard drive) and then upon finding that you really didn't need all that space after all, just adjust the sizes accordingly if it even becomes an issue...if it's not an issue, just leave them as is. And if it becomes an issue, I would get a second hard drive (say, external) where the excess could be stored.

With 600 GB of hard drive space, you seemingly have a lot of space.  Unless you edit videos or have *that* many audio files, I can't see you having much of an issue with hard drive space.  Say 60 GB for Vista, 60 GB for Ubuntu, 12 GB of swap (8GB RAM X 1.5), and the rest a second ntfs partition for both.

Oh, and just in case...I would create the second ntfs partition with a partition editor, like [GPartEd]("http://gparted.sourceforge.net/").  For the most part, Linux and associated software will handle ntfs partitions just fine, but I have heard of problems.

If you create the ntfs partition with GPartEd (also available on the Ubuntu Live CD), it should create an ntfs partition that most Linux software will handle without problem.  Not necessarily so with something that Vista will create.

It probably makes no difference by now, but it's just as easy to create it with one of the Partition Editors, and the resultant ntfs partition (or FAT32, if you so desire) can be read by Vista.

---

### Post by ibuclaw on 2009-04-04
> **-kg- said:**
> 12 GB of swap (8GB RAM X 1.5), and the rest a second ntfs partition for both.
I just noticed that ...

If you do have 8GBs of RAM, and you never use **hibernation**, my suggestion would be to then **not use any swap at all**!
With 8GBs, you have more than ample enough to run your machine and never have problems.

Regards
Iain

---

### Post by #include on 2009-04-06
That is correct, I have 8GB of Corsair Dominator memory.

---

### Post by #include on 2009-04-06
Thank you for the responses and discussion all. It has been very informative.

---

### Post by #include on 2009-04-30
Okay, I'm trying to do this.

I set up a 40GB Vista partition. A 40GB EXT3 partition for ubuntu, a 12GB SWAP, and the rest as a NFTS partition.

Vista is loaded correctly, made the other partitions from within UbuntuLIVE. Then did the install after a reboot (boot from cd), and at the installation menu it asks where to install it. I say the EXT3 partition, choose to format it, and say to mount to /home.

It says it cannot find the root partition/directory...

Help! What do I do to make this work?

---

### Post by Paqman on 2009-04-30
> **#include said:**
> That is correct, I have 8GB of Corsair Dominator memory.

You'll struggle to even use a tiny fraction of that. One option is to start putting things like your /tmp and browser cache into your RAM, since RAM is always going to be faster than disk access. I do both those and still never get above 2GB unless i'm running a fat VM.

---

### Post by Paqman on 2009-04-30
> **#include said:**
> a 12GB SWAP

Bit of a waste of space. Swap needs to equal RAM if you want to hibernate, but otherwise I wouldn't bother with more than 1GB. As mentioned above, with so much memory you could quite happily run with none.

---

