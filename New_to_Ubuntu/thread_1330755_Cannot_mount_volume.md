---
title: "Cannot mount volume"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by nodenet on 2009-11-18
I had dual boot Ubuntu and Vista.
Dropped the laptop lost the vista installation installed ntfs -config and was able to see my old windows files.

However it suddenly wouldnt let me mount drive. 
I went in as root and chmod and chown ed the directory
I have edited fstab.

See below and tell me what i can do

SESSION LOG


mark@mark-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c62b218

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10706    85995913+   7  HPFS/NTFS
/dev/sda2           10707       14593    31222327+   5  Extended
/dev/sda5           10707       14427    29888901   83  Linux
/dev/sda6           14428       14593     1333363+  82  Linux swap / Solaris
mark@mark-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9998437c-a7ae-4ec2-8bae-fc757d33d8e0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=d99001db-1246-69ba-d3b9-3502ba8b9090 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1    /media/disk    ntfs-3g    force    0    0mark@mark-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-25-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
mark@mark-laptop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk
fuse: failed to access mountpoint /media/disk: No such file or directory
mark@mark-laptop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force
fuse: failed to access mountpoint /media/disk: No such file or directory

---

### Post by Cheesemill on 2009-11-18
> **nodenet said:**
> failed to access mountpoint /media/disk: No such file or directory

You need to create the directory /media/disk before you try to mount a filesystem under it.

---

### Post by nodenet on 2009-11-18
How do i create a directory there and would i lose the vista files?

---

### Post by Cheesemill on 2009-11-18
You can create the directory using
```
sudo mkdir /media/disk
```
then
```
sudo mount -a
```
will mount the drive

You wont lose anything as you're creating the directory before you mount the file system.

---

### Post by nodenet on 2009-11-18
warning: no final newline at the end of /etc/fstab

is what comes back after mount command

---

### Post by nodenet on 2009-11-18
However it has worked.
Thanks

---

