---
title: "Not Grokking Partitions"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by selander on 2011-01-09
New to Linux; setting up a 16 drive NAS to hold company's video production files, Ubuntu server 10.04.

Coming from a Mac background where you have to first partition a drive, then format it with the 'filesystem.' Can't format without making a partition(s) first. Playing with mdadm and raid6, I have created a raid, /dev/md0, put the ext4 filesystem on it, mounted it and have successfully copied data to it. Unmounted, data of course inaccessible, re-mount and data is there again. Reboot works okay too. However, what has me a bit freaked out is that I NEVER partitioned the individual drives nor the array -- so why does the filesystem work? How could I even put a filesystem on it??   #fdisk -l reports "Disk /dev/sd_ doesn't contain a valid partition table" for each drive in the raid (sda, sdb, etc.) and, further, "Disk /dev/md0 doesn't contain a valid partition table"  And yet I'm writing data to it. 

How can this be? Are partitions not a requirement in Linux? Is it safe to use the /dev/md0 in this state, or will I have catastrophic data loss in the future?

 I've Googled quite a bit about this and have not come up with any answers.... everything makes it sound like you _must_ have at least one partition per drive.

Any enlightenment greatly appreciated.

---

### Post by coffeecat on 2011-01-09
I know little about creating filesystems in raw hard drives without partitions, but it is possible. I've seen it described in another thread, but I regret I can't find it at the moment. I even have an example at home - a digital dictation machine with its SDD formatted FAT16 with no partition table, or at least something that gives me interesting messages from the various command line partition tools.

To pick up another point: no, it is not normal in Linux not to have partitions. Most people use the ms-dos/mbr partition table because that's what their Windows-based machines come with, but Linux will work with the GUID partition table that Apple uses.

Out of interest, how did you create a filesystem in a drive with no partitions? I regret I know next to nothing about RAID, so I'd better say no more. The forum member who could talk authoritatively about this will probably be offline at the moment because of timezone differences.

---

### Post by selander on 2011-01-09
> **coffeecat said:**
> Out of interest, how did you create a filesystem in a drive with no partitions? I regret I know next to nothing about RAID, so I'd better say no more. The forum member who could talk authoritatively about this will probably be offline at the moment because of timezone differences.

I also intalled Webmin, and used its RAID module to create the RAID6 on brand new raw drives. (Had to install mdadm first.)

It gave me the option to put a filesystem on it, which I chose. However, that didn't seem to do anything, so from the terminal did mkfs.ext4 on md0 and away it went. I was curious to see what Webmin's module did for partitioning, so after the mkfs, I did an fdisk -l. Surprise, surprise, no partition tables, but the filesystem works! Hoping to find out if that's okay, or if I've set myself for loss of data down the road.

---

### Post by CharlesA on 2011-01-09
It probably created a partition on the array.

You can see if there's anything listed by running this:

```
sudo fdisk -l
```

---

### Post by selander on 2011-01-09
> **CharlesA said:**
> It probably created a partition on the array.

You can see if there's anything listed by running this:

```
sudo fdisk -l
```

Yep, that's what tells me none of the disks and the raid itself have no partition tables:  "Disk /dev/sd_ doesn't contain a valid partition table"

---

### Post by CharlesA on 2011-01-09
It should list the array as /dev/md0 or something like that.

Try using parted to see if it shows the drives as having valid partition tables. I have a feeling they are using GPT, but even in that case, fdisk should detect them as having GPT partition tables.

---

### Post by selander on 2011-01-09
> **CharlesA said:**
> It should list the array as /dev/md0 or something like that.

Try using parted to see if it shows the drives as having valid partition tables. I have a feeling they are using GPT, but even in that case, fdisk should detect them as having GPT partition tables.

Right; as I said in the original post, fdisk says there are no valid partition tables for the raid (/dev/md0) nor for any of the individual drives. It's quite long, but here's the output of fdisk -l (/dev/sdc is the boot drive, a 12GB 2.5" drive that is not part of the raid)

Output:
```
root@tera-nas:/home/nas-admin# fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 12.1 GB, 12072517632 bytes
255 heads, 63 sectors/track, 1467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000845e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1400    11241472   83  Linux
/dev/sdc2            1400        1468      545793    5  Extended
/dev/sdc5            1400        1468      545792   82  Linux swap / Solaris

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdg doesn't contain a valid partition table

Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdi doesn't contain a valid partition table

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdh doesn't contain a valid partition table

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0: 12002.4 GB, 12002393063424 bytes
2 heads, 4 sectors/track, -1364695552 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 24576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

---

### Post by selander on 2011-01-09
P.S. While I said this is a 16 drive NAS, I'm going to make two raids in it. This is the first one, with 8 drives. The other drives/raid are not installed yet.

---

### Post by CharlesA on 2011-01-09
Might want to check here: [https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)

---

### Post by selander on 2011-01-09
> **CharlesA said:**
> Might want to check here: [https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)

Hey, that is an _excellent_ link that I had not found yet. AND it answered my question -- you **can** raid whole disks, and install a file system, without making partitions! According to the linked wiki, the author of mdadm creates whole disk raids, without partitions. Fascinating. Linux continues to be a mind expander!

Now I gotta figure out how you mark a thread [SOLVED] on this forum.... ;-)

---

### Post by srs5694 on 2011-01-09
A couple of points. First, in reference to the below....

> **CharlesA said:**
> I have a feeling they are using GPT, but even in that case, fdisk should detect them as having GPT partition tables.

GPT includes a "protective MBR," which is a valid MBR data structure with a single disk-spanning partition of type 0xEE. Thus, a valid GPT disk *will always* be recognized by fdisk as being partitioned. Linux fdisk, in particular, also recognizes GPT structures (I'm not sure what it's using for this purpose, though), and puts up a warning to use GNU Parted when it detects GPT structures.

The protective MBR was designed explicitly to keep GPT-unaware utilities from messing with the disk and preventing the sort of confusion that selander describes. This brings me to the second point: Although you *can* create a RAID array on unpartitioned disks and use the array without partitions, I recommend against it. As you've discovered, the usual disk partitioning tools won't recognize that the disk is partitioned, so at some point down the road, something could get confused and be unable to do whatever it's supposed to do, or it might get confused enough to do damage. I don't know of any specific utilities that will definitely cause problems with your setup, but there are a *lot* of disk utilities out there, and there *could* be something that'll cause problems. Putting a partition table on the disk reduces the odds of such problems.

Another issue is flexibility: If you create a partition table on the disks, you may be able to use that at some point in the future to change how the disk is used. I'm not sure offhand if it's possible to reduce the size of the individual devices (partitions or disks) in a RAID array, but if it is, you might use that feature on a partitioned disk to create room for some other partition you'll end up needing in the future. Even if it's not presently possible to reduce the size of RAID component devices, this ability might conceivably be added in the future.

Overall, both these points are minor ones. If you've already put much data on your array, I wouldn't recommend starting over from scratch. If the effort isn't very great, though, you'll get a small bit of extra safety margin and a tiny bit of extra flexibility by using partitions on the disks to create your array.

---

