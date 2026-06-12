---
title: "grub gone wrong"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by patchido on 2009-05-06
i made a partition to install windows xp on my external HD that was used for ubuntu, now it has ubuntu and xp, and in the internal drive got vista
sdb1 ubuntu sdb2 swap sdb3 xp, and this is my menu.lst

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c209b65b-ace7-430f-bda0-e9ee0ac2c2ef ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c209b65b-ace7-430f-bda0-e9ee0ac2c2ef ro  single
initrd		/boot/initrd.img-2.6.27-11-generic


title		Ubuntu 8.10, memtest86+
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
chainloader	+1

```




the last 2 wont work, they are wrongly done, (not by me) xD

---

### Post by patchido on 2009-05-06
the funny thing is that Grub wasnt erased, windows didnt touch the MBR

---

### Post by Elfy on 2009-05-06
Check the partitions and menu list match

```
sudo fdisk -l
```

Grub counts from 0 - so sda1 is (hd0,0) sda2 - (hd0,1) sdb1 - (hd1,0) etc

---

### Post by patchido on 2009-05-06
> **forestpixie said:**
> Check the partitions and menu list match

```
sudo fdisk -l
```

Grub counts from 0 - so sda1 is (hd0,0) sda2 - (hd0,1) sdb1 - (hd1,0) etc

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317       14267   104023036    7  HPFS/NTFS
/dev/sda4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed260086

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5080    40805068+  83  Linux
/dev/sdb2            6993        7296     2441880    5  Extended
/dev/sdb3            5081        6992    15358140    7  HPFS/NTFS
/dev/sdb5            6993        7296     2441848+  82  Linux swap / Solaris

Partition table entries are not in disk order
```



here it is, i dont know what to put :S

---

### Post by patchido on 2009-05-06
plz, i need this :)

---

### Post by patchido on 2009-05-06
well, ive managed to get it, but i get an erro, i think it is because of windows, hmm ill check it tomorrow

---

### Post by patchido on 2009-05-06
this is what i get

```
Starting up...
NTLDR is missing
Press Ctrl+Alt+Del to restart
```

---

