---
title: "cant change HDD permissions"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by insanity99 on 2009-10-18
i got a new internal HDD and i couldn't find it in my media server. i checked the permission and is's set to root. i tried changing it with 'gksudo nautilus' but when i try to change it is keep reverting back to root instantly. 

help appreciated. thanks.

---

### Post by ajgreeny on 2009-10-18
You will need to use an edit of /etc/fstab to do what you want, I think.
Let's see the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```and it should be easy to do what you want.

---

### Post by SkyNet2029 on 2009-10-18
You need to edit the mount option for the drive in /etc/fstab to read 'user' or 'users'
 
I found a great post on fstab and mount points here [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
 
that goes into great length as to how and why of all of this. It's also downloadable as a .pdf for reference. How cool is that?

---

### Post by insanity99 on 2009-10-18
> **ajgreeny said:**
> You will need to use an edit of /etc/fstab to do what you want, I think.
Let's see the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```and it should be easy to do what you want.

neil@ubuntu:~$ sudo fdisk -l
[sudo] password for neil: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x574e76f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa461aa80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd25d95cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       17847   143355996    7  HPFS/NTFS
/dev/sdc2           17848       22946    40957717+   6  FAT16
/dev/sdc3           22947       60801   304070287+   6  FAT16
neil@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
neil@ubuntu:~$ 

this is the output. what next?

---

### Post by rhythmiccycle on 2009-10-18
when I installed a new internal hard drive just followed the steps on this page:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by ajgreeny on 2009-10-18
> **insanity99 said:**
> neil@ubuntu:~$ sudo fdisk -l
[sudo] password for neil: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x574e76f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa461aa80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd25d95cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       17847   143355996    7  HPFS/NTFS
/dev/sdc2           17848       22946    40957717+   6  FAT16
/dev/sdc3           22947       60801   304070287+   6  FAT16
neil@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
neil@ubuntu:~$ 

this is the output. what next?
So which is the new one you want to mount and be able to read and write?  We need to know that to be able to add the correct line to fstab.  Would I be right in thinking it's the 500GB disk?

---

### Post by insanity99 on 2009-10-19
> **ajgreeny said:**
> So which is the new one you want to mount and be able to read and write?  We need to know that to be able to add the correct line to fstab.  Would I be right in thinking it's the 500GB disk?

the new one is 1TB. but there is two, my old one which is fine i believe and my new one

---

### Post by halitech on 2009-10-19
did you use WUBI to install?

---

### Post by insanity99 on 2009-10-19
> **halitech said:**
> did you use WUBI to install?

yea i did

---

### Post by ajgreeny on 2009-10-19
I'll bow out in that case; I do not know enough about wubi and the differences it exhibits in comparison to a standard partitioned dual boot system.

---

### Post by halitech on 2009-10-19
I'm with ajgreeny, I've never used it but the way things were showing up as /host/ubuntu/disks/ had me thinking it was wubi. You may want to post down in the wubi subsection, I think you'll get better assistance down there.

---

### Post by insanity99 on 2009-10-19
ok thanks guys.

---

