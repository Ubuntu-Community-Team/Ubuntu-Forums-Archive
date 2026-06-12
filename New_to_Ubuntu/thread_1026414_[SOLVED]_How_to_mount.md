---
title: "[SOLVED] How to mount"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by mayagrafix on 2008-12-31
How do I mount an external USB hard drive which is formated in NTFS?

when I run fdisk in a CLT, I get this:

rafael@Inspiron:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c700c6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3555    28555506   83  Linux
/dev/sda2            3556        3648      747022+   5  Extended
/dev/sda5            3556        3648      746991   82  Linux swap / Solaris

[COLOR="SeaGreen"]Disk /dev/sdb: 6495 MB, 6495068160 bytes
255 heads, 63 sectors/track, 789 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005bbe6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         789     6337611    7  HPFS/NTFS[/COLOR]
rafael@Inspiron:~$

The first disk /dev/sda is my main HD, the one in green is the one I want to mount:D

Thanks for your great help!

---

### Post by wmoore on 2008-12-31
```
sudo mount -t ntfs /dev/sdb1 /mnt/mount-point
```

---

### Post by mayagrafix on 2008-12-31
Thanks for your reply. This is what I get:

rafael@Inspiron:~$ sudo mount -t ntfs /dev/sdb1 /mnt/mount-point

[COLOR="YellowGreen"]fuse: failed to access mountpoint /mnt/mount-point: No such file or directory[/COLOR]

rafael@Inspiron:~$

---

### Post by Tim Sharitt on 2008-12-31
I may be wrong but to be able to write to the partition it needs to be mounted as ntfs-3g
```
 sudo mount -t ntfs-3g /dev/sdb1 /mountpoint
```

---

### Post by Tim Sharitt on 2008-12-31
> **mayagrafix said:**
> Thanks for your reply. This is what I get:

rafael@Inspiron:~$ sudo mount -t ntfs /dev/sdb1 /mnt/mount-point

[COLOR="YellowGreen"]fuse: failed to access mountpoint /mnt/mount-point: No such file or directory[/COLOR]

rafael@Inspiron:~$

Where '/mnt/mountpoint' is you need to substitute an actual folder where you want the volume mounted.

---

### Post by Michael.Godawski on 2008-12-31
hi,

create a mount point
```
sudo mkdir /media/datapartition
```mount the partition:
```
sudo mount /dev/sdb1 /media/datapartition -t ntfs -o umask=0002,nls=utf8
```> 
The NTFS filesystem is mounted 'read only', so we can only copy things out of it, we cannot paste things into it or alter any files while they are in the NTFS filesystem.
OR:

you can use the fstab to mount the drive at boot:
make mount point
```
sudo mkdir /media/ntfsdata
```make a backup of fstab file
```
sudo cp /etc/fstab /etc/fstab_backup
```edit the fstab with
```
gksudo mousepad /etc/fstab
```add this line and save, reboot.

```
/dev/sdb1  /media/ntfsdata  ntfs ro,umask=0002,nls=utf8      0         0
```

Perhaps you will need to install these packages to mount the ntfs partition:
```

sudo apt-get install ntfs-3g ntfs-config ntfsprogs
```

---

### Post by mayagrafix on 2008-12-31
Thanks you guys, Ill get right on it :popcorn:

---

