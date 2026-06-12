---
title: "[SOLVED] Mounting ext3 hard drive"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Goll on 2008-12-22
I have 2 hard drives. sda.
I'm installed on one- the other I just formatted/recreated to ext3.

I searched for this, and they say to put it in fstab.
(I don't need this booting with ubuntu)- I just need access to my hard drive.
It says I don't have permissions to put anything into the drive, but it opens.

I need to set the permissions for this drive so that I am able to access it as a user.
I forgot the command to do it- what am I doing wrong or not doing?
Any help would be appreciated.

The other forum threads link to: [https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions) but I'm not seeing anything on the page.

My fstab: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=30b96fea-60f3-4df2-95c2-ca167689103b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b24510dd-8ec3-4145-9d68-054a49a74865 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I know, kind of, how to put it on the bottom- but the <dump> <pass> doesn't make sense to me.

---

### Post by nhasian on 2008-12-22
create a mountpoint like /data 

```
sudo mkdir /data
```

then you can mount it with

```
sudo mount /dev/sdb1 /data
```

assuming your 2nd hard disk is sdb and your mounting the first parition on it.

---

### Post by taurus on 2008-12-22
Do you know the mount point of the second harddrive?

```
sudo fdisk -l
cat /etc/fstab
df -h
```
All you have to do is change the ownership of the mount point (for the second harddrive) from root to your login name.  _Assuming_ the mount point is /media/drive and your login name is goll, you would do something like

```
sudo chown -R goll:goll /media/drive
ls -la /media/
```

---

### Post by Goll on 2008-12-22
> **nhasian said:**
> create a mountpoint like /data 

```
sudo mkdir /data
```

then you can mount it with

```
sudo mount /dev/sdb1 /data
```

assuming your 2nd hard disk is sdb and your mounting the first parition on it.

I'm sorry- you may not have gotten my edit (I kept putting more into the post)
It mounts; I just can't write to it. I can open the drive and all, but I can't do anything to it. :/

---

### Post by Goll on 2008-12-22
I'm sorry for posting twice.

---

### Post by Goll on 2008-12-22
> **taurus said:**
> Do you know the mount point of the second harddrive?

```
sudo fdisk -l
cat /etc/fstab
df -h
```
All you have to do is change the ownership of the mount point (for the second harddrive) from root to your login name.  _Assuming_ the mount point is /media/drive and your login name is goll, you would do something like

```
sudo chown -R goll:goll /media/drive
ls -la /media/
```

Excellent.
```
 sudo chown goll /media/disk
``` worked just fine for me.

I'd like to read more on that- unfortunately the documentation in the wiki section seemed empty.
I very much appreciate it.

---

### Post by Goll on 2008-12-26
> **taurus said:**
> Do you know the mount point of the second harddrive?

```
sudo fdisk -l
cat /etc/fstab
df -h
```
All you have to do is change the ownership of the mount point (for the second harddrive) from root to your login name.  _Assuming_ the mount point is /media/drive and your login name is goll, you would do something like

```
sudo chown -R goll:goll /media/drive
ls -la /media/
```

Now trying to do this in Debian. (I don't feel it's right to make another thread.

I've done: 
```

ajz3@debian:~$ **sudo chown ajz3 /media/disk/**
ajz3@debian:~$ **sudo mount /dev/sdb**
sdb   sdb1  sdb2  
ajz3@debian:~$ **sudo mount /dev/sdb /media/disk/**
mount: you must specify the filesystem type
ajz3@debian:~$ **sudo mount ext3 /dev/sdb /media/disk/**
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
**ajz3@debian:~$ **


```

I've also done the sudo mount, assigning the command to sdb1 instead of just the drive (Which I heard is what you're supposed to do.)

This is ext3, I don't know how to do this...

---

### Post by DavidBeijer on 2009-02-03
This all worked fine for me too, I also managed to edit my fstab file for automatically mounting the second harddisk, however sometimes after booting, sda and sdb are switched. So normally my Ubuntu is installed on sda, and my datadisk is on sdb. Then fstab (which tells Ubuntu to mount sdb1 to mnt/data) works. However, when they are switched, sdb is the drive with my Ubuntu installation, and sda is the data disk. fstab will then (off course) not mount that one to /mnt/data. Is there a way I can make sure that sda is my Linux disk, and sdb the data disk?

fdisk -l:
```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc05dc05d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac29ac29

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38157   306496071   83  Linux
/dev/sdb2           38158       38913     6072570    5  Extended
/dev/sdb5           38158       38913     6072538+  82  Linux swap / Solaris

```

fstab: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ad8f063d-6f48-40ab-8b84-35a673185d54 /               ext3    relatime,erro$
# /dev/sda5
UUID=b640dffa-a85f-4fe5-b1a8-b66a5e94a62a none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /mnt/data       ext3    defaults        0       0

```

---

### Post by Elfy on 2009-02-03
You could try using UUID for your data drive - run

```
blkid
```

It will return a code for your drives edit fstab to use that rather than the /dev/sdb1 you currently have to UUID=

---

