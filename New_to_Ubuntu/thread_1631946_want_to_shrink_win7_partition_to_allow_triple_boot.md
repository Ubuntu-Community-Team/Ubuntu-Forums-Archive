---
title: "want to shrink win7 partition to allow triple boot"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by neuro99 on 2010-11-27
Hi,

I've been using Ubuntu Lucid netbook remix in a dual boot with win7.

I would like to try out the latest version of ubuntu netbook by using a triple boot configuration - something I think will require me to shrink the windows partition, as I allocated most of the space to it. 

Here's how my current configuration looks in fdisk:

sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb54f27ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3        30801920   263516045   116357063    7  HPFS/NTFS
/dev/sda4       263516158   312580095    24531969    5  Extended
/dev/sda5       263516160   310458367    23471104   83  Linux
/dev/sda6       310460416   312580095     1059840   82  Linux swap / Solaris

/sda2 = RECOVERY partition, has flags 'boot' - not sure what this does but its 14gb size

/sda3 = win7 partition, 110gig size, mounted as /media/win for access from within ubuntu

the rest are I think for ubuntu

SO, I want to resize /sda3 win7 partition to create a space for the new version of ubuntu netbook remix, here are my questions/problems:

- do I need to defragment the win7 partition before resizing?

- Gparted won't let me resize it at the moment, it just says the minimum size for the partition is the same as the max size.

- there is an error, (incidentally?) that comes up on the partition when I unmount it from gparted which says something like 'warning:.....cluster xxxxx is referenced multiple times!)

sorry for the long question but just wanted to give as much info as poss

Thanks

---

### Post by oldfred on 2010-11-27
The * or boot flag is to windows the active partition. That is the boot partition for windows, even if your main install is in another partition.

It sounds more like you need to run chkdsk on the NTFS partition if that is the partition gparted says has issues.

Defrag will not hurt and may speed up the resize, but use the windows MMC to resize the windows partition. Then use gparted to move the extended partition left into the new free space. Then inside the extended you can create the new partition(s).

I prefer not to directly write into a windows system partition, reading is ok, but sometimes windows is not happy if too much activity occurs without its knowledge. Also in Ubuntu you see all  the hidden files & folders and  could accidentally modify or move one and cause problems. I prefer to create a shared NTFS partition for any data you may want in both installs. I also have multiple installs of Ubuntu (on different drives) and have a shared /data partition. 

Expanding an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

