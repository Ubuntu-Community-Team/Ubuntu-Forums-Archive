---
title: "Problem reformatting external (USB) HDD"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by tnek on 2009-03-01
I'm trying to reformat the HDD to ext2 instead of FAT32 and everything seems to go well, until I check the file system using fdisk -l again and it say "W95 FAT32 (LBA)" just like before the format. Why hasn't it changed?

I did a little test and created one file called a and another called A in the root of the disk. And it worked. As FAT32 doesn't allow that I guess it's ext2 after all, or? And if it is, I still wonder why fdisk -l doesn't give a correct report?

Here is how I reformatted the drive:
```
$ sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinderss 
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a431a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14029   112687911   83  Linux
/dev/sda2           14030       14593     4530330    5  Extended
/dev/sda5           14030       14593     4530298+  82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    c  W95 FAT32 (LBA)

$ sudo mke2fs -T ext2 -L external /dev/sdc1 
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=external
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
39075840 inodes, 156282320 blocks
7814116 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
4770 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

$ sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a431a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14029   112687911   83  Linux
/dev/sda2           14030       14593     4530330    5  Extended
/dev/sda5           14030       14593     4530298+  82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    c  W95 FAT32 (LBA)

```

---

### Post by taurus on 2009-03-01
Maybe reboot.

---

### Post by prinny42 on 2009-03-01
You need to partition the disk properly before changing its filesystem.

First, unmount the volume; then issue:
```
sudo cfdisk /dev/sdc
```

Make sure to omit the number.

Once you're in cfdisk, hit [d] to delete the existing partition.  It might complain about empty partitions or something, in which case you should just go down one and hit [d].  After that, hit [n] to create a new partition and [t] to change its type.  Choose "Linux."  Then hit capital [W] to write the partitions, and when it's done, hit [q] to quit.  Make sure to unmount the drive again if it remounts.

To make the new filesystem itself, I generally use the command
```
sudo mkfs -t ext2 (VOLUME NAME WITH NUMBER)
```

I label it separately with
```
sudo e2label (VOLUME NAME WITH NUMBER) (DESIRED VOLUME LABEL)
```

However, looking at the manual, your command looks mostly fine, but note that the uppercase "T" should be a lowercase "t":

```
sudo mke2fs -t ext2 -L external /dev/sdc1
```

It might behave oddly at first, just unplug and plug it back in (unmount first, of course, if necessary).  If you get a permissions error with it, just change the owner of its mount folder from root to you.

---

### Post by vanadium on 2009-03-01
You can just change the partition's system id type using fdisk, no need to repartition all over again. There is an advantage of using gparted, which does that automatically.

---

### Post by tnek on 2009-03-01
Thank you both! :-)

---

### Post by tehforum on 2009-03-01
I would have used gparted.

---

### Post by tnek on 2009-03-03
> **tehforum said:**
> I would have used gparted.
Yes. I didn't have it installed and thought it wouldn't be a big deal to get the device working without gparted, and it really wasn't. I have tried gparted now though, and it's quite an excellent tool. I'll definitely use it more in the future.

---

