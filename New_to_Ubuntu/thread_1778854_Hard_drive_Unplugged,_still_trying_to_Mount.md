---
title: "Hard drive Unplugged, still trying to Mount?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Super-Dan on 2011-06-09
I removed a hard drive, first formatting it then making sure it was deselected for auto mount!

Switched the PC off, unplugged drive and fired it back up

Get a message /sdc1 mounting S to skip M for manual repair.

So how do I stop it then? Doing my head in!!!! :D

4 days with Ubuntu and still learning :p

---

### Post by TeoBigusGeekus on 2011-06-09
You also need to delete it from your fstab file.
```
gksu gedit /etc/fstab
```
Can you post us the contents of the file?

---

### Post by Super-Dan on 2011-06-09
> **TeoBigusGeekus said:**
> You also need to delete it from your fstab file.
```
gksu gedit /etc/fstab
```
Can you post us the contents of the file?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc        proc  nodev,noexec,nosuid           0  0  
/dev/sda1  /            ext4  errors=remount-ro             0  1  
# swap was on /dev/sda5 during installation
/dev/sdg1  /media/sdg1  ntfs  nls=iso8859-1,umask=000,user  0  0  
/dev/sdb1  /media/sdb1  ext4  user                          0  0  
/dev/sdc1  /media/sdc1  vfat  defaults                      0  0

---

### Post by TeoBigusGeekus on 2011-06-09
Delete this line
```
/dev/sdc1 /media/sdc1 vfat defaults 0 0
```
This way, ubuntu won't try to mount it on startup.

By the way, this file, fstab, controls the partitions that are mounted automatically on startup.

---

### Post by Super-Dan on 2011-06-09
> **TeoBigusGeekus said:**
> Delete this line
```
/dev/sdc1 /media/sdc1 vfat defaults 0 0
```
This way, ubuntu won't try to mount it on startup.

By the way, this file, fstab, controls the partitions that are mounted automatically on startup.

Wow!

How do you learn about stuff like this / remember the commands!?

---

### Post by TeoBigusGeekus on 2011-06-09
Just lurk more in the forums.

[Here's]("http://ubuntu-manual.org/download/10.10/en_US/screen") a good book to get you started with ubuntu and [another one]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") to get you started with the command line.

---

