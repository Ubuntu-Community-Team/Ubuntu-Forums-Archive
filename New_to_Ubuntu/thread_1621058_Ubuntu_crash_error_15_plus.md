---
title: "Ubuntu crash error 15 plus"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by sez567 on 2010-11-13
Please help.  Had Ubuntu 10.04 installed and kept freezing - mouse and keyboard didn't work etc.  Downloaded and installed kernel pre-empt as I have  a satellite connection which has a lot of latency.  Computer froze and I couldn't get response from keyboard/mouse so did a hard restart.  Now have error 15.  Downloaded live CD for Ubuntu 10.10 and attempt to install but get ubi-partman failed with exit code 10 error.  
fdisk -l reads:I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cb63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       59339   476640486   83  Linux
/dev/sdc2           59340       60799    11727450    5  Extended
/dev/sdc5           59666       60799     9108823+  82  Linux swap / Solaris
/dev/sdc6           59340       59643     2441817   83  Linux
/dev/sdc7           59644       59665      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/dm-1: 500.1 GB, 500095254528 bytes
255 heads, 63 sectors/track, 60799 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cb63

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   *           1       59346   476696713+  83  Linux
/dev/dm-1p2           59347       60801    11687287+   5  Extended
/dev/dm-1p5           59347       60801    11687256   82  Linux swap / Solaris
Please tell me the process exactly as I have no idea how to get around linux.  Many thanks

---

### Post by diablo75 on 2010-11-14
/dev/sdc1 [COLOR="Red"]1[/COLOR] 59339 476640486 83 Linux (1 indicates this partition houses the default /boot and judging by the size of the partition, is the primary partition for the first install of Linux)


/dev/sdc2 59340 60799 11727450 5 Extended  (Think of this as a container for the following partitions)


/dev/sdc5 59666 60799 9108823+ 82 Linux swap / Solaris (Original swap partition)

/dev/sdc6 59340 59643 2441817 83 Linux (I would suspect this is a second / partition for a second install of Ubuntu, intended to replace the original / above (sdc1).  The size is barely enough to support the whole OS as it's a little less than 2.5 GB in size, which will cause problems).

/dev/sdc7 59644 59665 176683+ 82 Linux swap / Solaris (Secondary install's swap)

So, if you have anything on this system from the original install that you want to save, you should use the Live CD to access the sdc1 partition (you should have a shortcut in your Places menu that will say something like "450 GB Filesystem" and in that find a folder called /home).  Once you find this folder you should back it up to an external hard drive and then use the Live CD to do a fresh install.  When it gets to the part about Drive Partitioning, tell it to "use the whole drive" (which will erase all the partitions you have on there and start from scratch).  Then move copy the backed up /home back to the new install.

The /home folder houses a folder for each user on the PC.  If you open it up, you'll see a folder named after you (or rather, your username that you'd login with).  When you reinstall, use the same username as you used to use so when you copy the /home folder from the external drive back to the new install, it will merge the contents of the old and new /home, which will result in a lot of personal settings and data being restored as if your computer never crashed (or almost).

---

### Post by sez567 on 2010-11-14
Thanks -when I boot from live CD I don't get the hard drive listed so I can select it.  There are no other volumes listed in "places"

---

### Post by diablo75 on 2010-11-14
> **sez567 said:**
> Thanks -when I boot from live CD I don't get the hard drive listed so I can select it.  There are no other volumes listed in "places"

Since sdc1 appears to be the partition you need to access, you can try to mount it manually via a terminal window.

Click Applications>Accessories>Terminal and paste in the following:

```
sudo mount /dev/sdc1 /mnt

```

This should create a new shortcut in the Places menu.

---

### Post by sez567 on 2010-11-14
when I "sudo mount /dev/sdc1 /mnt"  I get "special device /dev/sdc1 does not exist"!

---

### Post by diablo75 on 2010-11-14
Could you run **sudo fdisk -l** one more time and paste the output?

---

### Post by sez567 on 2010-11-14
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cb63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59339   476640486   83  Linux
/dev/sdb2           59340       60799    11727450    5  Extended
/dev/sdb5           59666       60799     9108823+  82  Linux swap / Solaris
/dev/sdb6           59340       59643     2441817   83  Linux
/dev/sdb7           59644       59665      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/dm-0: 500.1 GB, 500095254528 bytes
255 heads, 63 sectors/track, 60799 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cb63

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       59346   476696713+  83  Linux
/dev/dm-0p2           59347       60801    11687287+   5  Extended
/dev/dm-0p5           59347       60801    11687256   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
 
I don't know why the disk identifier keeps changing sda-sdb-sdc

---

