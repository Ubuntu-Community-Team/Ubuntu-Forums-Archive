---
title: "Partitioning error"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by Raoul Duke, esq. on 2011-01-11
Hey Now...

I have a 500GB drive with 2 partitions and 137GB of free space. When I try to create a new partition in the free space I get the following error: 

Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdb, start=33280, size=137000230400, type=0x83
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 137000231424, type 0x85)
Entering MS-DOS extended parser (offset=32256, size=137000231424)
readfrom = 32256
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 137000263680, size 363104985600, type 0x83)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
Error: Invalid partition table on /dev/sdb -- wrong signature 0.
ped_disk_new() failed


MBR file corrupt? What do I need to edit and how? I haven't exactly mastered Terminal. 

Any help would be greatly appreciated.

Thanks

---

### Post by Quackers on 2011-01-11
What program are you using to do this please?
And what has been done to the HDD previously?

---

### Post by Raoul Duke, esq. on 2011-01-12
Using the standard Disc Utility that comes with Ubuntu.

I initially formatted it with Disc Utility as an  Ext4 drive (/dev/sdb) and created two partitions: Music (137GB) and Movies (363GB). It was working fine until we had a power outage. The Movies partition is still accessible and seems to be working fine.

---

### Post by srs5694 on 2011-01-12
Please post the output of the following command:

```

sudo fdisk -lu /dev/sdb

```

Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags; this will preserve the column formatting, which improves legibility vs. not using those tags.

---

