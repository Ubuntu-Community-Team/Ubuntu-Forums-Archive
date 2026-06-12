---
title: "Permission and Ownership problems on hard drives - ubuntu 10.04"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by anigodin on 2010-05-26
Hello,

I insalled 10.04 a few weeks ago. I also have windows 7 installed.

Up untill recently I had a similar system (XP + ubuntu 8.04) and I was able to read and write to any hard drive with no problem.

I have to hard drives:
The main drive which contains 3 partitions: windows (system), ubuntu (3 partitions) and a data partition.
The secindery drive is only data.

I cant write to any of the partitions which are not ubuntu. the partitions are owned by root.
I read about it here and some other places but it was all to technical for me.
I'll be grateful if someone can explain in a simple way how to make those partitions writebale.

I'm attaching fdisk -l result:

Left]Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x156bd6bd

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 3824 30716248+ 7 HPFS/NTFS
/dev/sdb2 3825 5040 9764864 83 Linux
/dev/sdb3 5162 19456 114820609 f W95 Ext'd (LBA)
/dev/sdb4 5040 5162 976896 82 Linux swap / Solaris
/dev/sdb5 7649 19456 94847728+ 7 HPFS/NTFS
/dev/sdb6 5162 7648 19972096 83 Linux

Partition table entries are not in disk order

Disk /dev/sda: 41.0 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99839983

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4982 40017883+ 7 HPFS/NTFS


Many thanks!

---

### Post by oldfred on 2010-05-26
You need to understand ownership & permissions.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Only after you have some idea of settings then you can use:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

### Post by Morbius1 on 2010-05-26
***STEP 1: Find out how the system sees your partitions***

You've done that:
> [COLOR=Blue]/dev/sda1 * 1 4982 40017883+ 7 HPFS/NTFS[/COLOR]

[COLOR=Blue]/dev/sdb1 * 1 3824 30716248+ 7 HPFS/NTFS[/COLOR]
/dev/sdb2 3825 5040 9764864 83 Linux
/dev/sdb3 5162 19456 114820609 f W95 Ext'd (LBA)
/dev/sdb4 5040 5162 976896 82 Linux swap / Solaris
[COLOR=Blue] /dev/sdb5 7649 19456 94847728+ 7 HPFS/NTFS[/COLOR]
/dev/sdb6 5162 7648 19972096 83 Linux***STEP 2: Create mount points for your partitions to live in*** ***( these are just suggestions ):***

Open Terminal:
```
sudo mkdir /media/WinXP
sudo mkdir /media/Data
sudo mkdir /media/BigData
```*** STEP 3: Add lines to /etc/fstab/ to have these partitions mount at boot:***

```
/dev/sdb1 /media/WinXP ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sdb5 /media/Data ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda1 /media/BigData ntfs defaults,nls=utf8,umask=007,gid=46 0 0
```In all these cases it will mount the ntfs partitions:
Owner = root
Read / write access by owner and group and no one else ( umask = 007 ).
All local login users will be able to read and write to those partitions ( gid = 46 which is plugdev - all local login users are members of plugdev by default )

This is old school and except for the fact that it uses UUID numbers instead of sdxy is exactly the way Ubuntu would have set those partitions in fstab had you used the manual partitioning option during the install.

If you really want to own the mount points then you can add **uid=1000** to the options list but you really don't need to since you are part of the plugdev group and already have full access.

---

### Post by anigodin on 2010-05-28
> **oldfred said:**
> You need to understand ownership & permissions.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Only after you have some idea of settings then you can use:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

I've installed PySDM and it worked like a charm. thank you very much!
I can now save to those hard drives. :-)

---

### Post by oldfred on 2010-05-28
I actually prefer Morbius1's way as it gives you control over all settings, but for new users the pySDM sometimes works and sometimes seems to need some settings changed.

---

### Post by ep_swat on 2010-08-24
Or if your an uber n008 like me you can just use Gparted and format your drive as an NTFS partition, but thats only if it is an additional drive. I added an additional 250gig drive and was having a hard time getting to write stuff to it, damn permissions, lol, so I did a NTFS partition and I am now able to create, read, write with no issues.

---

### Post by Morbius1 on 2010-08-24
> **ep_swat said:**
> I added an additional 250gig drive and was having a hard time getting to write stuff to it, damn permissions, lol, so I did a NTFS partition and I am now able to create, read, write with no issues.
Formatting a new drive to NTFS because you didn't realize that all you had to do was a :
```
sudo chown ep_swat /mountpoint
```seems a bit drastic ;)

---

