---
title: "Major IDE SDisk problem while formatting help :("
date: 2009-03-18
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-03-18
Well what I did was hook up this IDE scan disk thing and I wanted to put the iso image on it (like a usb stick) because its only 2 gig. So I did this  [http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)   and got to a part where it said it wasnt formatted by FAT in my terminal.

So I tried to format it by  umount /dev/sda1 then mkfs.vfat /dev/sda1


not when I try to mount it again it saids  

unable to mount the volume.

Details:
Mount: wrong fs type, bad option, bad superblock on /dev/sda1,   missing codepage or helper program, or other error   In some cases useful infor is found in syslog  - try dmesg | tail or so


root@eric:~# dmesg | tail
[  325.430390] Buffer I/O error on device sdc1, logical block 15755
[  325.430395] lost page write due to I/O error on sdc1
[  325.430402] Buffer I/O error on device sdc1, logical block 15756
[  325.430407] lost page write due to I/O error on sdc1
[  325.430421] Buffer I/O error on device sdc1, logical block 6573312
[  325.430427] lost page write due to I/O error on sdc1
[ 2205.970382] VFS: Can't find ext3 filesystem on dev sda1.
[ 2219.167055] VFS: Can't find ext3 filesystem on dev sda1.
[ 2254.476877] VFS: Can't find ext3 filesystem on dev sda1.
[ 2366.186566] VFS: Can't find ext3 filesystem on dev sda1.



any Ideas? I would use the usb-creator to do it but it wouldnt even see this flash drive, I guess cause its hook on the IDE?

---

### Post by achase79 on 2009-03-18
it must be listed in /edt/fstab as ext3 still.  You can fix this by pressing alt-F2 then running ```
gksu gedit /etc/fstab
``` and change the drive labeled /dev/sda1 from ext3 to vfat.

---

### Post by ericeclifford on 2009-03-18
I just did didnt work. still has exact same errors.

---

### Post by achase79 on 2009-03-18
how are you trying to mount the drive?

---

### Post by ericeclifford on 2009-03-18
root@eric:~# mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab


Here is my etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5295748e-5635-47db-81b0-44f42d289026 /               vfat    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e03bb511-ebf5-4b84-8e6d-93596113d714 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by t0p on 2009-03-18
I've got a couple of usb flash sticks, they automatically mount when I stick them in.  They're not listed in my /etc/fstab file.  What about running **gparted**? Hit **Alt+F2** and type in the box

```
gksudo gparted
```

No sign of the stick there?

(I use gparted to format my sticks anyway.  Nice and simple, a GUI etc.)

---

