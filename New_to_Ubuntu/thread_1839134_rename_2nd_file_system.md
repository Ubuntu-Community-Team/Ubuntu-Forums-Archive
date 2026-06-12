---
title: "rename 2nd file system"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by DennisMesa on 2011-09-05
I have 2 hard drives on my system. The first has my operating system, and the second has all my saved files. When I try to change the name from /media/36 digit name to /media/1_gig_hd I get 2 messages.
If it's mounted it says the system is busy.
If it's unmounted it says it doesn't exist.
any ideas?

Zorin 5 64 bit

---

### Post by papibe on 2011-09-05
You can change it, but the method to do it is different depending on which file system it has, and if it is an external usb (usually means automounted), or an internal hard drive.

Could you post the result of these two commands?
```
$ sudo mount -l

$ sudo fdisk -l
```
Regards.

---

### Post by axatrikx on 2011-09-05
u can boot from a gparted live cd and do the changes.

---

### Post by DennisMesa on 2011-09-05
Here is what happens.

dennis@dennis-Zorin-5:~$ sudo mount -l
[sudo] password for dennis: 
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dennis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dennis)
/dev/sr1 on /media/My Disc type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500) [My Disc]
gvfs-fuse-daemon on /home/patti/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=patti)
/dev/sdb6 on /media/181a82fa-21c7-4560-a10a-ca03f68dbefc type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb8 on /media/b53a2923-6f4a-4935-9f01-f103edbe4177 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1 on /media/5b770457-a33d-44c6-8d71-216fe4ad2800 type ext4 (rw,nosuid,nodev,uhelper=udisks)
dennis@dennis-Zorin-5:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00008a21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60019   482096128   83  Linux
/dev/sda2           60019       60802     6287361    5  Extended
/dev/sda5           60019       60802     6287360   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066b87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       69837   560962399+  83  Linux
/dev/sdb2           69837      121602   415798273    5  Extended
/dev/sdb5          120850      121602     6034432   82  Linux swap / Solaris
/dev/sdb6           86958      120590   270147584   83  Linux
/dev/sdb7          120590      120849     2086912   82  Linux swap / Solaris
/dev/sdb8           69837       86697   135425024   83  Linux
/dev/sdb9           86697       86957     2092032   82  Linux swap / Solaris

Partition table entries are not in disk order
dennis@dennis-Zorin-5:~$ 

I'm still pretty new at this, so any help would be appreciated.

---

### Post by DennisMesa on 2011-09-05
gparted??

---

### Post by DennisMesa on 2011-09-05
(Solved) i downloaded g parted live.  I was able to change the label from 36 digits to a manageable 5 digits. This makes it much easier to work in that partition.
Thanks for the help:)

---

