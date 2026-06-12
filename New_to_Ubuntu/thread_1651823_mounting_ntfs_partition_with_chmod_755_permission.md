---
title: "mounting ntfs partition with chmod 755 permission"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by astrob0t on 2010-12-23
i wanted to set chmod 755 permissions to my external hdd (ntfs partition)..
As i was not able to change it though terminal because it asked to mount the drive as root..

so i install ntfs-3g..

but with it i am able to set permissions 777 or 333 only...

any way of setting the permission to 755 exclusively because i want to share some files on my ext hdd on a LAN..

i also read in various forums that setting chmod perssioons to ntfs partitions is not possible in linux., as linux only allows ext2 , ext3, ext4 or any linux based partition to be able to change permission...
IS THIS TRUE ???


PLZ HELP ME TO MOUNT MY EXTERNAL HDD(NTFS PARTTION) AS ROOT AND TO BE ABLE TO SET 755 PERMISSION ...

---

### Post by astrob0t on 2010-12-23
the link [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) did enlighten me in some ways..but i want to set my hdd at 755..nothing else..plz help


:-(

---

### Post by deanjm1963 on 2010-12-23
You should try and install ntfs-config which will allow you to enable read/write permissions. And yes, you CANNOT set linux style permissions on an NTFS drive.

Hope this helps.

---

### Post by sandyd on 2010-12-23
> **aviatsit said:**
> i wanted to set chmod 755 permissions to my external hdd (ntfs partition)..
As i was not able to change it though terminal because it asked to mount the drive as root..

so i install ntfs-3g..

but with it i am able to set permissions 777 or 333 only...

any way of setting the permission to 755 exclusively because i want to share some files on my ext hdd on a LAN..

i also read in various forums that setting chmod perssioons to ntfs partitions is not possible in linux., as linux only allows ext2 , ext3, ext4 or any linux based partition to be able to change permission...
IS THIS TRUE ???


PLZ HELP ME TO MOUNT MY EXTERNAL HDD(NTFS PARTTION) AS ROOT AND TO BE ABLE TO SET 755 PERMISSION ...
Your not mounting the drive correctly.

post output of
```

sudo fdisk -l
```

---

### Post by astrob0t on 2010-12-23
> **sandyd said:**
> Your not mounting the drive correctly.

post output of
```

sudo fdisk -l
```

```

username@username-ubuntu-pc:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00085f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      194560   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              25         268     1952768   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3             268       19458   154141696   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb190

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

---

### Post by oldfred on 2010-12-24
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by astrob0t on 2010-12-24
> **oldfred said:**
> understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/mount/](https://help.ubuntu.com/community/mount/)
[https://help.ubuntu.com/community/filepermissions](https://help.ubuntu.com/community/filepermissions)

ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
howto: Mount ntfs partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)


great tutorial !!!
Simply great..no words..

Thanks oldfred..
My system up and running..

-=solved=-

---

### Post by oldfred on 2010-12-24
Glad it helped. :)

It was getting late, so I just posted some info that is usually helpful. I usually have to add lots of verbiage.

---

