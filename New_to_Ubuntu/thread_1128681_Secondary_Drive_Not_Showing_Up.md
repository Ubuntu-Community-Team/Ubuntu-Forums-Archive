---
title: "Secondary Drive Not Showing Up"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by TAllen013 on 2009-04-17
I've got a secondary internal hard-drive that will only sporadically show up in my Xubuntu 8.10 installation.  It will always show up in Gnome though.  Does anyone know what the problem could be?

Thanks in advance for any responses.

---

### Post by GCoffee on 2009-04-19
Is it mounted, or do you mean it doesnt show up in disk mounter?

---

### Post by superprash2003 on 2009-04-19
post output of **sudo fdisk -l**

---

### Post by TAllen013 on 2009-04-25
Disk /dev/sda: 61.4 GB, 61473226752 bytes
240 heads, 63 sectors/track, 7940 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x21b121b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7940    60026368+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0e7953fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       32301   244195528+   7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40b2987e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS



THE DRIVE THAT I'M CONCERNED WITH IS THE 250GB ONE.  IT IS NOT SHOWING UP IN "PLACES" DROP-DOWN OR IN THE MEDIA FOLDER.  DOES ANYONE KNOW HOW I CAN GET XUBUNTU TO RECOGNIZE IT AS A DRIVE LIKE IT DOES THE OTHER TWO.

---

### Post by TAllen013 on 2009-04-25
UPDATE:  I just noticed that the drive does show up when I go into a program and choose to open a file.  (For example, if I open Movie Player and choose open, it does display the drive.)

But why doesn't it show up in Places or in the left panel of the File Manager?

---

