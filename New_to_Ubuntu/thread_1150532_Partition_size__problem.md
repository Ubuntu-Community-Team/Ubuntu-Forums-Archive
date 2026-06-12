---
title: "Partition size  problem"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by devil_ankur18 on 2009-05-06
this is the output df -H of my ubuntu 8.10 desktop 

root@cc-desktop:~# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               20G   8.2G    11G  44% /
tmpfs                  1.1G      0   1.1G   0% /lib/init/rw
varrun                 1.1G   558k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G   2.9M   1.1G   1% /dev
tmpfs                  1.1G    13k   1.1G   1% /dev/shm
lrm                    1.1G   2.1M   1.1G   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda6              109G    93G    11G  90% /downlaod
/dev/sda7               26G    17G   8.9G  66% /windows



check out the entry for /dev/sda6 , its used(93) + Available(11) < Size(109) 

Where is 6 GB gone  :confused:

please help me out

---

### Post by skymera on 2009-05-06
Well /dev/sda6 is mounted on /downlaod

Go have a look what's taking up the space.

---

### Post by tomcheng76 on 2009-05-06
post your "fdisk -l" and "free -m"

---

### Post by kpkeerthi on 2009-05-06
5% of the drive's total space is reserved for the super-user (root) so that the operating system can still write to the disk even if it is full.

---

### Post by unutbu on 2009-05-06
ext2/ext3/ext4 filesystems have "reserved blocks". This is space that is reserved for root to use. It is counted as part of the total size of the filesystem, but it is not counted as part of the amount "Used" or "Available".

The default amount of reserved space is 5%. 
5% of 109G is 5.45G.
109-(93+11) = 5G.

If you use "df" instead of "df -H" I think the discrepancy will be smaller.

You can change the amount of reserved space on an ext* filesystem


```
sudo tune2fs -m1 /dev/sda6    # Set reserved blocks to 1% of total space

sudo tune2fs -r51207 /dev/sda6 # Set reserved blocks to 51207 4K-blocks* = 200 MiB
```

*For a 109G filesystem, the default block size is 4 KiB per block. To find out the block size on sda6, run```

sudo tune2fs -l /dev/sda6 | grep "Block size"
```

---

### Post by KIAaze on 2009-05-06
Hehe, I noticed a similar problem recently: [http://ubuntuforums.org/showthread.php?t=1145503](http://ubuntuforums.org/showthread.php?t=1145503)

Just found this, but haven't checked if it explains the exact number of space I had used (5% from 10GB would have been about 512 MB for me):
[http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/](http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/)
[http://www.chineselinuxuniversity.net/articles/17988.shtml](http://www.chineselinuxuniversity.net/articles/17988.shtml)
[http://books.google.com/books?id=wOGUuoHUyAEC&pg=PA47&lpg=PA47&dq=linux+df+used+%2B+available+does+not+equal+size&source=bl&ots=OEkupul51V&sig=YMNmKvRjl2xoeoJbjXj5rfbeR7I&hl=en&ei=82kBSoXvCMGOsAaVwej0Dg&sa=X&oi=book_result&ct=result&resnum=1#PPA48,M1](http://books.google.com/books?id=wOGUuoHUyAEC&pg=PA47&lpg=PA47&dq=linux+df+used+%2B+available+does+not+equal+size&source=bl&ots=OEkupul51V&sig=YMNmKvRjl2xoeoJbjXj5rfbeR7I&hl=en&ei=82kBSoXvCMGOsAaVwej0Dg&sa=X&oi=book_result&ct=result&resnum=1#PPA48,M1)

---

### Post by devil_ankur18 on 2009-05-06
> **tomcheng76 said:**
> post your "fdisk -l" and "free -m"


root@cc-desktop:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5e1f5e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2437    19575171   83  Linux
/dev/sda2            2438       19457   136713150    5  Extended
/dev/sda5            2438        2952     4136706   82  Linux swap / Solaris
/dev/sda6            2953       16325   107418591   83  Linux
/dev/sda7           16326       19457    25157758+   b  W95 FAT32

root@cc-desktop:~# free -m
             total       used       free     shared    buffers     cached
Mem:          1979       1930         48          0         15       1260
-/+ buffers/cache:        654       1324
Swap:         4039          4       4034

---

### Post by devil_ankur18 on 2009-05-06
> **unutbu said:**
> ext2/ext3/ext4 filesystems have "reserved blocks". This is space that is reserved for root to use. It is counted as part of the total size of the filesystem, but it is not counted as part of the amount "Used" or "Available".

The default amount of reserved space is 5%. 
5% of 109G is 5.45G.
109-(93+11) = 5G.

If you use "df" instead of "df -H" I think the discrepancy will be smaller.

You can change the amount of reserved space on an ext* filesystem


```
sudo tune2fs -m1 /dev/sda6    # Set reserved blocks to 1% of total space

sudo tune2fs -r51207 /dev/sda6 # Set reserved blocks to 51207 4K-blocks* = 200 MiB
```*For a 109G filesystem, the default block size is 4 KiB per block. To find out the block size on sda6, run```

sudo tune2fs -l /dev/sda6 | grep "Block size"
```

Thanx , it works :guitar:
I use 

```
tune2fs -m0.8 /dev/sda6
```Now output of df -H is
```

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               20G   8.2G    11G  44% /
tmpfs                  1.1G      0   1.1G   0% /lib/init/rw
varrun                 1.1G   558k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G   2.9M   1.1G   1% /dev
tmpfs                  1.1G    13k   1.1G   1% /dev/shm
lrm                    1.1G   2.1M   1.1G   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda6              109G    93G    16G  86% /downlaod
/dev/sda7               26G    17G   8.9G  66% /windows

```

---

