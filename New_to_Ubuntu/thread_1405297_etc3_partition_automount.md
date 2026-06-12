---
title: "etc3 partition automount"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by poliltimmy on 2010-02-12
I have tried many tutorials to get my data partition to mount on boot. It now mounts on boot as an icon but with a twist, it is just link to the desktop and all the folders also as separate icons on the desktop. Additionally the Data link in Nautilus is also now a link to the desktop. I can access the files just fine using the icons. But I simply just want the Data partition to mount on boot and an icon for the drive to show up as it should.

```
timmy@timmy-pawpawsliltoy:~$ blkid
/dev/sda1: LABEL="Data" UUID="fe19a025-ee84-4838-9fcc-d04a3f70a614" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="2d58255d-b86e-4357-9641-83cc3d68de73" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="cc5fd58d-3adb-47e5-a9b1-760d6f5e54f9" 

```

```
timmy@timmy-pawpawsliltoy:~$ sudo gedit /etc/fstab
[sudo] password for timmy: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2d58255d-b86e-4357-9641-83cc3d68de73 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=cc5fd58d-3adb-47e5-a9b1-760d6f5e54f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sda1
UUID=fe19a025-ee84-4838-9fcc-d04a3f70a614     /home/timmy/Desktop     ext3 auto,rw,defaults 0 0

```
Any help will be greatly appreciated! Thanks, Timmy

---

### Post by joberly on 2010-02-12
The line that says /home/timmy/Desktop.

Change it to something else! Like /media/<name of drive>

You have to create the folder in /media with superuser privileges.

---

### Post by poliltimmy on 2010-02-12
> **joberly said:**
> The line that says /home/timmy/Desktop.

Change it to something else! Like /media/<name of drive>

You have to create the folder in /media with superuser privileges.

Would that be sda1 or Data, also will sudo su be appropriate.  Also what is the code 
if you would not mind.

Done deal with the line change. The directory was already created in my attempts. Thanks a bunch!!!

---

