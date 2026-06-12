---
title: "Installing ubuntu partition wants all my space"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by zxy on 2009-03-29
Ok so i'm trying to install ubuntu but now the partition wants all my space... i just wanted to give it about 15-20gigs not all of it.

---

### Post by Hospadar on 2009-03-29
If you go to "manual partition" during the installer you can fine tune your paritions and what gets installed where.

The main option is really just to allow you to quickly and conveniently install to the whole drive if that's what you want.

---

### Post by presence1960 on 2009-03-29
> **zxy said:**
> Ok so i'm trying to install ubuntu but now the partition wants all my space... i just wanted to give it about 15-20gigs not all of it.
 Choose the guided resize which isn't in this shot, but it should be above the guided use entire disk option. Then use your mouse to resize the partition graphically by sliding the end of the partition to adjust it's size

---

### Post by zxy on 2009-03-29
i cant do the resize thing anymore but i can do the manual thing

---

### Post by presence1960 on 2009-03-29
Here is the correct screenshot...sorry

---

### Post by presence1960 on 2009-03-29
> **zxy said:**
> i cant do the resize thing anymore but i can do the manual thing

before proceeding why don't you run this in terminal and post the output here ```
sudo fdisk -l
``` that is a lowercase L not the number one. This will show the partitions already on your hdd and the filesystems on them.

---

### Post by zxy on 2009-03-30
erm....where is the terminal?

---

### Post by Paqman on 2009-03-30
Applications > Accessories > Terminal

---

### Post by zxy on 2009-03-31
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe56bbab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       38913   311025664    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by Paqman on 2009-04-03
Well that's fine. If you look at the screenshot for guided partitioning you showed, your NTFS partition will be shrunk down, and Ubuntu installed after it.

It's a very small disk though. do you have Windows installed on the NTFS partition currently? If so you probably won't have room to dual-boot on that drive, as Windows is likely to need a lot more than 10GB.

---

