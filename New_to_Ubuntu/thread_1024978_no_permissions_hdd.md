---
title: "no permissions hdd"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by jsaulter on 2008-12-29
I am sorry if I am posting this in the wrong section, but I am really green to Linux. I try to view one of the two hd in my tower my storage drive and it says permissions denied. I was at one point able to view and change files, but not now. I tried  gksudo nautilus  and can only view the files and cant do anything else. Again I am very new to Linux and the terminal. Please help me.

---

### Post by Michael.Godawski on 2008-12-29
hey, 

can you please post the output of this terminal command? 

applications > accessories > terminal

```

sudo fdisk -l
```

---

### Post by jsaulter on 2008-12-29
jamie@jbone:~$ gksudo
jamie@jbone:~$ gksudo
jamie@jbone:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25a525a4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0049e09e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    b  W95 FAT32
jamie@jbone:~$

---

### Post by jsaulter on 2008-12-29
Thanks for the help so quickly it's the 80 gig I can't do anything with anymore.

---

### Post by Michael.Godawski on 2008-12-29
can you please also post the output of this command:

```
cat /etc/fstab
```

The fstab file tells us what permissions are linked to that fat32 partition.

---

### Post by jsaulter on 2008-12-29
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e2c9249b-25e4-4c5b-a4a3-edff6c7c2f33 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e2bf9165-a302-4175-bbbd-94b0d7359f5c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
jamie@jbone:~$

---

### Post by taurus on 2008-12-29
```
sudo mkdir /media/hdb1
sudo mount -t vfat /dev/hdb1 /media/hdb1 -o umask=000
ls -la /media/hdb1
```

---

### Post by jsaulter on 2008-12-29
I don't know if I am doing it correct or not but it wont work it says
cannot open directory /media/hdb1: Permission denied
And I thank you for all your help I know noobs are frustrating.

---

### Post by taurus on 2008-12-29
What about 

```
sudo blkid
```

---

