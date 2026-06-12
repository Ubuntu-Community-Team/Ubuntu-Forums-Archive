---
title: "Mount Points"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by ferret man on 2010-02-28
I would like to mount a partition onto a folder called "/storage". I know that all I should have to do is add a line to my fstab, but I am having trouble finding what to add. Can someone help? 
 my fdisk -l : 

drake@drake-laptop:~$ sudo fdisk -l
[sudo] password for drake: 

Disk /dev/sda: 15.4 GB, 15408046080 bytes
255 heads, 63 sectors/track, 1873 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+  83  Linux
/dev/sda2            1790        1873      674730    5  Extended
/dev/sda3            1307        1789     3879697+  83  Linux
/dev/sda5            1790        1873      674698+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001970d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         486     3903763+  83  Linux
/dev/sdb2             487         969     3879697+  83  Linux
/dev/sdb3   *         970        2275    10489856   83  Linux
/dev/sdb4            2276       60801   470110095    5  Extended
/dev/sdb5            2276        2359      673792   82  Linux swap / Solaris


my fstab:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c5fd7c27-c289-4f46-a22c-b4ba156ed11d /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=0ed529c2-0934-45e0-8764-80335dc225b7 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=85292dd4-45f6-4704-94ea-24eb51883dea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by ferret man on 2010-02-28
Whoops, the partition I want to mount is /dev/sdb1. 
Right now, it mounts to /media/disk.

---

### Post by garvinrick4 on 2010-02-28
System/Admin/gparted. Go to gparted drop down on upper left.
  It will open its partition table up. Right click on partition you want to mount
  and choose label. Lets say you call it backup. type backup in for label. Ok now see
what it says sdb1 or something like that. Close gparted.

Now open a terminal.
Make a directory:  sudo mkdir /media/backup
Now mount: " sudo mount /dev/sdb1 /media/backup"   without qoutes            space after sdb1 
To unmount: " sudo umount /media/backup"  without quotes,                                      not a typo umount is right

Get it now, it is always called /media/backup from now on. 
All drives or partitions have there own sda5 or sba1 or sda7. Use the one
it is in gparted or can run "sudo fdisk -l"  without quotes small L that is also.
Once you label something it is always that to mount or unmount. /media/backup
or whatever you name it. 
Must make a directory (folder) for any new device. /dev is always followed by its partition # /sdb1 for example.

---

### Post by ferret man on 2010-02-28
That doesn't exactly work the way I want it to. For example, I use a separate home partition, so the contents of /dev/sda3 are loaded onto the folder /home whenever I boot up. I would like for it to occur that when I boot up, the contents of /dev/sdb1 are loaded onto a folder called /storage.

---

### Post by undecim on 2010-02-28
The recommended way to do this is using a UUID in your fstab line. To do this, first find the UUID of the drive you want by running "ls -l /dev/disk/by-uuid" in a terminal. You should get an output something like```
total 0
lrwxrwxrwx 1 root root 10 2010-02-28 15:20 047856bd-c99a-42a4-861e-901ee99853fd -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-02-28 15:20 a96e4b88-33f3-41c3-8083-361f83bb6814 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-02-28 15:20 ee5beda8-c33e-48ed-ad71-1c3ceb726571 -> ../../sda5
```
each of those long numbers near the end are the UUIDs of each partition on my system.

Now, If I wanted, for example, to always mount my /dev/sda2 to /storage, I would add this line to my /etc/fstab file.```
UUID=a96e4b88-33f3-41c3-8083-361f83bb6814 /storage ext4 defaults
```

This is because according the the ls command earlier, a96e4b88-33f3-41c3-8083-361f83bb6814 is the UUID for my /dev/sda2, and I know from creating that partion that it was an ext4 filesystem. The "defaults" at the end are the mount options. If this is a removable drive, you may want to reaplce this with "user" which will allow you to mount it without root access if you plug it in after booting.

If you don't care to use UUIDs, you can use /dev/sdb1, instead of UUID=..., but that may cause problems when you add or remove a drive.

---

