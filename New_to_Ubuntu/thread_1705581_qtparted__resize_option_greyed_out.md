---
title: "qtparted  resize option greyed out"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by beew on 2011-03-12
Hi,

I have been using gparted and find it easy and intuitive to use. However, I have recently made a KDE installation and want to also try out some of its native apps so I installed qtparted, now I want to resize an existing partition (ext4) and find that the resize option is greyed out. The partition is not mounted and I could have resize it easily with gparted.

What am I missing?

Thanks.

---

### Post by Rubi1200 on 2011-03-12
Hi,
could you post a screenshot of how qtparted sees the partitions?

---

### Post by beew on 2011-03-12
Here it is. Can't see anything unusual, the layout is a bit odd, the two partitions on the left were created after Windows was deleted and as a result I couldn't put them in  a extended partition.

---

### Post by Rubi1200 on 2011-03-12
It's been a long time (Knoppix 2005 :smile:) since I used qtparted; what do the littles tuxes next to the partitions represent?

Do you need to unmount those partitions perhaps?

---

### Post by beew on 2011-03-12
> **Rubi1200 said:**
> It's been a long time (Knoppix 2005 :smile:) since I used qtparted; what do the littles tuxes next to the partitions represent?

Do you need to unmount those partitions perhaps?

The little tuxes apparently represent Ubuntu! There are no little tuxes in the other partitions even though they also are Linux (LMDE / and /home)

The partitions are unmounted. I think qtparted unmounts them by default anyway

---

### Post by Rubi1200 on 2011-03-12
I assume you want to shrink either sda1 or sda4?

From the screenshot, it appears this should be possible.

Just out of curiosity, can you post the output of ```
sudo fdisk -lu
```

---

### Post by beew on 2011-03-12
Hi,

Yes, I am trying to shrink sda4 to create a new partition for Ubuntu 11.04 for testing purpose.

I should clarify that sda is my internal hard drive. But I am actually plugged into sdb which is an external drive that I use as a portable multi-linux install.

  >  Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    30476287    15237120   83  Linux
/dev/sda2   *    76324864   105621503    14648320   83  Linux
/dev/sda3       105623550   156299263    25337857    5  Extended
/dev/sda4        30476288    76324863    22924288   83  Linux
/dev/sda5       105623552   152395775    23386112   83  Linux
/dev/sda6       152397824   156299263     1950720   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b6bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    41945087    20971520   83  Linux
/dev/sdb2        41947134   625141759   291597313    5  Extended
/dev/sdb5        41947136   125833215    41943040   83  Linux
/dev/sdb6       125835264   130029567     2097152   82  Linux swap / Solaris
/dev/sdb7       130031616   171974655    20971520   83  Linux
/dev/sdb8       171976704   243286374    35654835+  83  Linux
/dev/sdb9       374124544   478351359    52113408    7  HPFS/NTFS
/dev/sdb10      243288423   259771049     8241313+  83  Linux
/dev/sdb11      259771113   275386229     7807558+  83  Linux
/dev/sdb12      275388278   300554101    12582912   83  Linux
/dev/sdb13      300556150   338304885    18874368   83  Linux



---

### Post by kansasnoob on 2011-03-12
Right click the partition in question and check "information":

[ATTACH]185855[/ATTACH]

---

### Post by beew on 2011-03-12
> **kansasnoob said:**
> Right click the partition in question and check "information":

[ATTACH]185855[/ATTACH]

Here it is. On my system the option is "property" rather than "information" :)

---

### Post by Rubi1200 on 2011-03-12
The only other thing I can think of at this moment is the fact that it says the device is busy (lower left hand of the screenshot).

---

### Post by beew on 2011-03-12
That is odd because I am on sdb and sda is not mounted. If I right click the drive in qtparted the option 'set active' is avaliable, I take it to mean that the drive is not active now.

---

### Post by Rubi1200 on 2011-03-12
Perhaps you need to try this without sdb plugged in?

---

### Post by beew on 2011-03-12
My kde OS and qtparted is install in sdb. :)

I could always do the partition with gparted if nothing works. I have a Mavarick install in sdb which has gparted.  I have done it many times and never had a problem. I just want to try something native in kde. :)

---

### Post by beew on 2011-03-12
Never mind. Just did some googling, It turns out that qtparted is long dead. There has been no development in qtparted since 2005 and it doesn't support resizing ext3 (let alone ext4). For a while people trying to use qtparted to resize ext 3 would have to first convert it to ext2, resize and then convert back. I am going to uninstall it and install the kde-partition-manager.

Thanks for all the reply.

---

### Post by Rubi1200 on 2011-03-13
Well, I am glad you finally got things sorted out.

---

