---
title: "two home folders"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by emtjr928 on 2009-02-28
I feel kinda lame asking this but here goes. I have been using since Dapper now intrepid.my install has three partitions,/, /home, /swap While trying to set up to use remastersys, I noticed that I have a home folder on / and one on my /home partition. Is this normal?
the data in these is identical.
Is this hhhow it should be?
Thanks,
Ed

---

### Post by Bölvaður on 2009-02-28
This may have happen because you didn't mount it as /home during the installation. You can add the /home partition in fstab so it will be auto mounted and just make links of Documents, Music... all the directories you use and make those links replace the direcotries on the / partition.


*added*
please notice that this is an easy fix... may not be very pretty but it works.

---

### Post by emtjr928 on 2009-02-28
I think it does mount in fstab? Here is mine.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=72d940d7-4904-45c3-a9d1-e3d722d3181d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=e6240924-5c2b-4f3d-acda-13e53451f085 /home           ext3    relatime        0       2
# /dev/sda1
UUID=1e624d5a-4e3b-48b1-af28-3a5f154550aa /media/storage  ext3    relatime        0       2
# /dev/sda6
UUID=adee6531-7a89-48b2-bb45-484c73827704 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1        
UUID=6e3c7645-56b5-45be-96f4-27d5560f836e /media/backup   ext3
defaults     0        2
usbfs /proc/bus/usb usbfs auto 0 0
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=125,devmode=664	0	0

---

### Post by emtjr928 on 2009-02-28
Here is my main hdd. I do have a second drive dev/sdb1.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92619261

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6068    48741178+  83  Linux
/dev/sda2   *        6069       14593    68477062+   f  W95 Ext'd (LBA)
/dev/sda5            6069        8601    20346291   83  Linux
/dev/sda6            8602        8729     1028128+  82  Linux swap / Solaris
/dev/sda7            8730       14593    47102548+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e365

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

---

### Post by miegiel on 2009-02-28
> **emtjr928 said:**
> I feel kinda lame asking this but here goes. I have been using since Dapper now intrepid.my install has three partitions,/, /home, /swap While trying to set up to use remastersys, I noticed that I have a home folder on / and one on my /home partition. Is this normal?
the data in these is identical.
Is this hhhow it should be?
Thanks,
Ed

Your /home get mounted in your / :) this is where it's always mounted if you have /home on a separate partition.

---

