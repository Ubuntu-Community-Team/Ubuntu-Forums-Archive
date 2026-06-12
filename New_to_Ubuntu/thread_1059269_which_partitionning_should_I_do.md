---
title: "which partitionning should I do?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by vblanche on 2009-02-03
Hi,

here is my system:
SATA drive 160Gb with windowsXP32-bit installed.
SATA drive 1TB

I'm trying to setup a dual-boot system, so I installed ubuntu8.10 and resized (via guided installation) the 160GB HDD to get 80GB for windows and 80GB for linux.

Now, what should I do with the 1TB HDD?
I thought I would go for 2x500GB partitioning, but what file system should I use? primary + ext2? ext3? extended?

thanks
vini

---

### Post by Eisenwinter on 2009-02-03
I'd use (if possible) ext4.

I think you should create, like you said, 2 partitions.

One should be NTFS, for storing files under Windows, and the other one should be ext4, or ext3, to store files in Linux.

I've recently created a random folder under my root file system, called MountPoint.
It's used to just mount random devices, but well, that's so off topic here.. heh.

Go into your root file system, and create a directory, called "Storage" or whatever else you want.

Partition the 1TB drive through fdisk, or cfdisk, or even GParted, if you prefer a graphical environment.

Add the newly created partition into fstab, give it a mount point, file system, etc.

Create another partition, this time NTFS, and use Windows to (insert word here, I'm drunk and lost train of thought) I guess "attach" it there.

---

### Post by 4Orbs on 2009-02-03
I would suggest 2 partitions... One of them very large and formatted to NTFS, the other relatively small and formatted to FAT32. Make permissions on both universally read and write. Windows XP will automatically mount both at bootup and you can use the XP defragmenting utility to keep them clean and smooth running. Ubuntu can read and write to either with no problems. The FAT32 partition will allow you to copy files from a Mac, Playstation or other system that requires fat. In the end you will have 1TB of common storage for both systems (or any new system, should you decide to triple boot).

For mounting the other partitions onto Ubuntu, I recommend installing the Storage Device Manager (pysdm). It makes mounting and unmounting a snap.
```
sudo apt-get install pysdm
```

---

### Post by vblanche on 2009-02-04
Hi,

thanks for your replies.

But if I want to setup this 1TB HDD under linux, which file system should I use with Gparted?

thanks
vini

---

### Post by OldGrey on 2009-02-04
As you are intending to just have one partition I believe a primary with ext3 should do the trick.

---

### Post by billgoldberg on 2009-02-04
For the one TB drive:

It depends, you could use fat32 or ntfs.

I think fat32 can only handle files upto 4gb and together with ntfs they need to be defragmented on a regular basis.

You could use ReiserFS or ext3. There are Windows drivers available for those filesystem so windows can read (write?) to them.

I would go for the latter.

---

### Post by vblanche on 2009-02-04
> **OldGrey said:**
> As you are intending to just have one partition I believe a primary with ext3 should do the trick.I thought 2 x 500GB...just because I thought that 1TB should be partioned, but I may be wrong. What do you think?

---

### Post by vblanche on 2009-02-04
> **billgoldberg said:**
> You could use ReiserFS or ext3. so maybe ext3 then...primary or logical? > **billgoldberg said:**
> There are Windows drivers available for those filesystem so windows can read (write?) to them.
do you mean: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by mikechant on 2009-02-04
Personally I wouldn't use ext4 until it's been around for another year or two. Even if it's really stable, you'll probably come across some tools that don't support it yet.

If you don't know what your future needs will be, I'd recommend setting up a single partition at the start of the disk with only part of the space and leave the rest unallocated for now (say you have 300Gb of data, maybe just use half of the disc - 500Gb - for your single partition). It's fairly quick and easy to grow a partition (as opposed to moving it, which can take ages).

As for the filesystem - if you spend most time in Linux, ext3 is probably best since although Linux can read/write NTFS reliably, I believe it's rather slow. You'll need ext2/3 drivers in windows as mentioned above. If you spend most time in Windows, use NTFS and take the performance hit in Linux.

---

