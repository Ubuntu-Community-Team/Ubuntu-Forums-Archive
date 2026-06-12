---
title: "does this make my other disk work?"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by donnerblitz on 2009-08-24
mke2fs -j /dev/sdb1

it is the wrong file system or something

i want it to be like mine which is ext3, whatever that means.

it is defiantly sdb1 i did this:
```

sudo fdisk -l
[sudo] password for me: 

Disk /dev/sda: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x148f148e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1186     9526513+  83  Linux
/dev/sda2            1187        1229      345397+  82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009c871

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1245    10000431    7  HPFS/NTFS

```

sorry for the silly question i just wanted to check with the wizards :)

---

### Post by wojmur on 2009-08-24
What are you actually trying to achieve, would be my first question. Are you trying to wipe the pre-existing, but no longer needed, Windows on your second drive and use the reclaimed space for your ubu?

---

### Post by donnerblitz on 2009-08-24
yes i have done that now, i did this:
```
$ sudo mkfs -j /dev/sdb1
```
then i ran gparted to make a new partition and rebooted. now it says i cant copy to the disk because i don't own it! well i could try waving the receipt in front of my web-cam but i don't think thats what it means some how.

help :)

---

### Post by Gen2ly on 2009-08-24
Good question.  Formatting a partition will destoy any data on it.  If you are shure type mkfs.[2x-tab] in the terminal for options.

---

### Post by donnerblitz on 2009-08-24
now when i checked
```
$ sudo fdisk -l
[sudo] password for me: 

Disk /dev/sda: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x148f148e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1186     9526513+  83  Linux
/dev/sda2            1187        1229      345397+  82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009c871

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1245    10000431   83  Linux

```so thats good, then it wouldn't let me copy my stuff there so i did:
```
gksudo nautilus
``` and changed the owner to me.

i think it works now. i can copy my stuff there now :)

---

