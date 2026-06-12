---
title: "SSD and partitioning"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by Green Mars on 2010-06-23
So after leaving ubuntu behind me for a while, I decided to install it again on my brand new SSD (OCZ Agility 60GB).

I've used the ubuntu live cd to align the SSD using fdisk (according to OCZ tutorial). All is well, but after this is done I've to install ubuntu.

So when I come to the setup wizard for making partitions a few questions come to mind;

1. Since I've aligned the SSD do I need to manually create "/" en "/home" partitions or instead just let ubuntu use the entire disk?
2. I also read a lot about moving /tmp cache to RAM, but does that mean I don't have to create a swap partition anymore?

Here is how I aligned my SSD.

```

$ sudo fdisk -H 32 -S 32 /dev/sda
The number of cylinders for this disk is set to 15711.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): o
Building a new DOS disklabel with disk identifier 0x8cb3d286.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

The number of cylinders for this disk is set to 15711.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-15711, default 1): 2
Last cylinder, +cylinders or +size{K,M,G} (2-15711, default 15711):
Using default value 15711
Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 83
Command (m for help): w
The partition table has been altered!
Calling ioctl() to re-read partition table.
Syncing disks.

```

---

### Post by Paqman on 2010-06-23
> **Green Mars said:**
> 
1. Since I've aligned the SSD do I need to manually create "/" en "/home" partitions or instead just let ubuntu use the entire disk?


Up to you. Creating different partitions manually is different from aligning them for an SSD. If you want a seperate /home, create one. Otherwise just let the installer create the default setup.

> 
2. I also read a lot about moving /tmp cache to RAM, but does that mean I don't have to create a swap partition anymore?


Swap and /tmp are different. /tmp is used to temporaily cache data on the drive (things like Flash videos are buffered there). Swap works like extra RAM, it's used for running apps.

If you've got the RAM, moving /tmp to a ramdisk is a good option. It's much faster, and saves writes to your SSD.

If you want, you can reduce the system's tendency to use swap by [dialling the swappiness down]("https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?"). If you have plenty of RAM then there's no reason you can't turn swappiness down to 10 or even 0. What this means is that your system won't touch swap until the RAM is totally full, which is how it should be IMO.

Some people run with no swap partition at all. I tend to keep a small one hanging around just in case.

---

### Post by Green Mars on 2010-06-23
> **Paqman said:**
> Up to you. Creating different partitions manually is different from aligning them for an SSD. If you want a seperate /home, create one. Otherwise just let the installer create the default setup.


Thank you for your reply. So in other words, if yo manually create new partitions for / and /home these partitions aren't aligned anymore?

After I've aligned the SSD with fdisk it's actually aligning a new partition instead of just the SSD.

---

