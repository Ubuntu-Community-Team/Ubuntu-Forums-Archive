---
title: "Filesystem size discrepancies"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by night_fox on 2009-04-15
My Terabyte external hard disk arrived today, with FAT32 and 1.76Gb of useless windows software on it including McAffee in every language. The minimum requirements were Windows 200, Windows XP and Windows vista, so I reformatted it to ext3! I made a 2Gb FAT32 partition at the end to put some windows programs that can access ext3. All partitioning was done in gparted.

Can anyone explain the following discrepancies?

```
# fdisk -l
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bdfef42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121346   974711713+  83  Linux
/dev/sdb2          121347      121601     2048287+   b  W95 FAT32

```

so my drive has almost exactly 1 decimal terabyte.

GParted tells me my ext3 partition is 930 binary gigabytes, which I can understand. A binary gigabyte is bigger than a decimal one. Now I go into Nautilus and make it work out the size of everything on there. free space: 648.4 GB, files: 219.6 GB. Total: 868GB. Interestingly (868/0.998 )*1.024^6 is almost exactly decimal 1TB. Where is the bug? Nautilus, GParted, fdisk, or my understanding?

---

### Post by unutbu on 2009-04-15
Please post the output of 

```
df
```

---

### Post by night_fox on 2009-04-15
Thanks for replying unutbu, the output of df corresponding to that hd is pasted below:
```
# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb2              2044276      2956   2041320   1% /media/AppsHereCanSeeOtherPartition
/dev/sdb1            959416680 244636128 666044968  27% /media/jd

```

---

### Post by unutbu on 2009-04-15
```

                          df                      GParted (GiB)           
               ---------------------------    ---------------------
	       total   free  avail   used      total  unused   used   
sdb1 (GiB)    914.97 681.67 635.19 233.30     930.
sdb1 (GB)     982.44 731.94 682.03 250.51     998.58 

```

df and Nautilus reports the size of your filesystems.
GParted (and fdisk) reports the sizes of your partitions.

The filesystem sits inside the partition, sort of like a filing cabinet inside of a room, except that the filing cabinet practically fills the room.

Every filesystem (such as ext3) has a scheme for remembering its directory structure and where files are physically located in the partition. That scheme requires some hard drive space to store, but is not counted as part of the filesystem itself. This accounts for the discrepancy between "used" sizes reported by GParted versus df (and Nautilus). The amount of "used" space as reported by GParted will always be greater than the amount of "used" space reported by df.

The total size of sdb1 as reported by GParted is about 930 GiB.
The total size of the filesystem in sdb1 as reported by df is  about 915 GiB.
The ratio is 930/915 = 1.017. 

From time to time I have measured this ratio on partitions/filesystems that I have made, and this ratio always seems about the same. So your numbers are in agreement with my numbers. 

So there is no unexplained discrepancy between GParted and df.

Regarding the apparent discrepancy between df and Nautilus:

The ext3 filesystem has "reserved blocks". This is space that is reserved for root only.
Its purpose is to save the system from becoming log-jammed if the user were to fill up the entire filesystem. It also helps reduce filesystem fragmentation. By default, 5% of the total space available to the filesystem is dedicated to reserved blocks.

The total size of sdb1 as reported by df is the total space available including reserved blocks.
The total size of sdb1 as reported by Nautilus is the total space available excluding reserved blocks.

The total size of the filesystem in sdb1 as reported by df is about 915 GiB.
Since we expect Nautilus to be 5% less, we should expect 
The total size of the filesystem in sdb1 as reported by Nautilus to be about 869.25 GiB.

When Nautilus says the total free space is 868 GB, I think it is using "GB" to mean "GiB".

I don't have an explanation for the difference between 869.25 and 868.

Generally, I think your setup looks fine because there is no unexplained discrepancy between df and GParted (and fdisk), and I have more confidence in the numbers they report than the numbers that Nautilus reports.

---

### Post by unutbu on 2009-04-15
PS: I used the "units" program/package to convert from 1K-blocks (KiB) to GB and GiB.

For example:
```

% units
2445 units, 71 prefixes, 33 nonlinear units

You have: 959416680 KiB
You want: GiB
	* 914.97105
	/ 0.0010929308
You have: 959416680 KiB
You want: GB
	* 982.44268
	/ 0.0010178711
```

---

### Post by night_fox on 2009-04-15
Thanks very much unutbu. That was a great explanation. I'd thank you if the feature hadn't been deleted from the forum.

=D>

---

