---
title: "swap area glitch!!!"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-09-22
I had defined 200MB of swap area at the time of installation but currently system monitor is showing 800+ MB of swap area. How to fix it?

I have a second problem, my Gparted is showing that my ubuntu root drive is having 456MB of space free but I am facing many problem as i do not have any disk space left. There may be relation b/w the two problem. What is the final solution for these problems

Thank You in advance...

---

### Post by drs305 on 2009-09-22
Please post the results of the following:
```

df -h

```

A screenshot of your gparted screen may also be useful in further posts.

---

### Post by eshant_engineer on 2009-09-22
Do we have any tools for ubuntu to manage system like to manage physical memory and to defragment disk or any related things?


> Please post the results of the following:

```

df -h
```



```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9             7.7G  7.2G  154M  98% /
tmpfs                 1.3G     0  1.3G   0% /lib/init/rw
varrun                1.3G  220K  1.3G   1% /var/run
varlock               1.3G  4.0K  1.3G   1% /var/lock
udev                  1.3G  188K  1.3G   1% /dev
tmpfs                 1.3G   88K  1.3G   1% /dev/shm
lrm                   1.3G  2.5M  1.3G   1% /lib/modules/2.6.28-15-generic/volatile
overflow              1.0M 1016K  8.0K 100% /tmp
/dev/sda8              20G   17G  3.8G  82% /media/DISK1_VOL3
/dev/sda6              17G   13G  4.0G  76% /media/disk
/dev/sda2              17G   13G  4.6G  74% /media/disk-1
/dev/sda7             5.5G  2.9G  2.6G  53% /media/DISK_VOL3

```

---

### Post by drs305 on 2009-09-22
> **eshant_engineer said:**
> Do we have any tools for ubuntu to manage system like to manage physical memory and to defragment disk or any related things?

Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="DarkRed"]/dev/sda9             7.7G  7.2G  154M  98% /[/COLOR]**
/dev/sda8              20G   17G  3.8G  82% /media/DISK1_VOL3
/dev/sda6              17G   13G  4.0G  76% /media/disk
/dev/sda2              17G   13G  4.6G  74% /media/disk-1
/dev/sda7             5.5G  2.9G  2.6G  53% /media/DISK_VOL3

Your system partition is indeed almost completely full. A 8GB system partition is ok and meets the minimum size necessary to run Ubuntu. However, it leaves little room for storing data files in your /home folder. If you have a lot of data stored in your Ubuntu installation you should consider moving it to another location if possible.

I wrote a guide on finding lost disk space. In this case, your partition is probably just too small and it being full is not being caused by major problems or misplaced backups.  

The guide does provide ways to increase free size, such as:
```

sudo apt-get autoclean
sudo apt-get clean

```

You can also make sure your trash bin and root's trash bin are empty.

Here is the link:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

For the swap issue, please post:
```

sudo fdisk -l  # That is a lowercase L

```

As for fragmentation, the linux file system is designed not to need defragmentation - another advantage over those *other* OS's.

---

### Post by eshant_engineer on 2009-09-22
This is the result:-(additionally i am attaching Gparted shot which is showing more unused space)
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdba3dba3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         196     1574338+   7  HPFS/NTFS
/dev/sda2             197        2415    17824117+   7  HPFS/NTFS
/dev/sda3            2416        9729    58749705    f  W95 Ext'd (LBA)
/dev/sda5            2416        3276     6915951    7  HPFS/NTFS
/dev/sda6            3277        5370    16820023+   7  HPFS/NTFS
/dev/sda7            5371        6081     5711076    7  HPFS/NTFS
/dev/sda8            6082        8685    20916598+   7  HPFS/NTFS
/dev/sda9            8686        9704     8185086   83  Linux
/dev/sda10           9705        9729      200781   82  Linux swap / Solaris


```

---

### Post by drs305 on 2009-09-22
Your options, if you need more space and have already run through the space restoring tips from the guide I linked to, are to shrink some of the ntfs partitions in the extended partition. (Or mvoe personal data out of your *HOME* partition.)

The easiest way to get a bit of breathing room for linux would be to shrink sda8 (Vol 3) and then expand sda9. You could do the same for other partitions, but to get that free space into the linux partition will mean moving a lot of partitions around.

If you want to take from space from sda8:
1. Defrag sda8 and back up the data elsewhere if possible. Defrag from within Windows.
2. Shrink sda8. If you have a Windows partitioner, use it. Otherwise, gparted will work fine.
3. Boot from a LiveCD to the Ubuntu Desktop. You will be working with the Ubuntu system partition, which must be unmounted.
4. If you have already reduced the size of sda8, the free space should be to the left and adjacent to sda9 (linux). If you haven't already reduced the size, umount sda8 and shrink it now. 
5. Make sure sda9 and swap are not mounted. (No "Keys" icons next to the partitions in the lower panel).
6. Expand sda9 to incorporate the free space on the left. This may take 15-30 minutes or longer. Don't interrupt the process.

Your swap appears to be slightly less than 200MB. I am not sure what your System Monitor is displaying.

---

### Post by eshant_engineer on 2009-09-22
Ya I know that how to do shring and expand..

Thank You

---

