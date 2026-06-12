---
title: "automount"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by konsta82 on 2009-07-11
How can I mount fat32 partition on startup ?
I have jaunty with ext4 on dell 1525

---

### Post by NESFreak on 2009-07-11
[http://ubuntuforums.org/showpost.php?p=7598418&postcount=5](http://ubuntuforums.org/showpost.php?p=7598418&postcount=5)

replace ntfs with vfat

---

### Post by konsta82 on 2009-07-11
man , it's not working
this is how my fstab looks like

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=c8354ff2-11f2-4f94-97b6-28ccffa3489c /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=217fde02-826e-4ca7-bbd0-633c19364046 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=[F67E-53A7] /media/disk       vfat    defaults,nls=utf8,umask=007,gid=46 0       1

---

### Post by Elep.Repu on 2009-07-11
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[edit]this-to
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by lncoll on 2009-07-11
> **konsta82 said:**
> How can I mount fat32 partition on startup ?
I have jaunty with ext4 on dell 1525

First you must know what partition is the disk.

The way to know; open a terminal, type: 
```
sudo fdisk /dev/sda
```
, enter your password, type: p, now you can see a list of partitions in your hard disk, write down the first part of the line where the partition you want to mount is, example: /dev/sda3.

Pulse q to exit from fdisk.

Create a folder where mount it, example: /dos

Now edit /etc/fstab with your prefered editor, must use sudo to gain write access to the file.

Edit or add a line to automount this partition, like this:

```
/dev/sda3 /dos -t vfat defaults,umask=007  0       1
```

Note I've used the examples above, /dev/sda3 and /dos change as your needs.

Next time you boot the partition will be automounted, if you want to test before reboot try in a console:

```
mount /dev/sda3
```

also must work:

```
mount /dos
```

That's all folks  :popcorn:

---

### Post by NESFreak on 2009-07-11
im sorry, the uuid should be without the brackets. also as incoll says you could replace the "uuid" part with the "/dev/whatever" part, as outputted by either blkid or fdisk.

note that the fdisk part only works for your first sata disk (/dev/sda), while blkid works for all partitions on all harddisks.

---

### Post by konsta82 on 2009-07-20
it's working

this is how my fstab looks like now

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=c8354ff2-11f2-4f94-97b6-28ccffa3489c /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=217fde02-826e-4ca7-bbd0-633c19364046 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda3  
 UUID=1875-09B3    /media/disk   vfat  umask=000      0     0


it is important to define umask,in order to be authorized to write on that partition
thanks all of you !

---

