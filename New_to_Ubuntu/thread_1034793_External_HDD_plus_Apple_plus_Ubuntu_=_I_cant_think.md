---
title: "External HDD plus Apple plus Ubuntu = I cant think of a better problem title sorry..."
date: 2009-01-09
forum: New to Ubuntu
---

### Post by skizeee on 2009-01-09
Ok,

I have all my music stored on an external HDD 1TB with about 200 gigs of music.

I usually connect this HDD to my now old intel Apple Macbook and use iTunes etc... I lent this HDD to my flatmate who I installed ubuntu onto his computer (couldnt be happier). The music is not DRM is all my own etc...

However he had a problem with his external screen resolution and found the solution on this forum ALT+F4 or something everything of his works fine now, but when he tried to access my music everything appeared corrupted/locked/not-there. I cant explain it any better than that only that when I plug the HDD into my 8.10 running eeepc is that now there is a padlock on the folders and the contents is corrupted or encrypted looking. The Mac cant even open the music folder.

Im no real expert on this neither is my friend unless he slipped up somewhere and isnt telling me I dont know whats happened. Just that I cant access anything...

Plz help!

Thanks

---

### Post by computermacgyver on 2009-01-09
Please include the output of:
```
lsusb
```

and ```

gksu fdisk -l
```

You should run these in a terminal by selecting Applications->Accessories->Terminal . Please copy and paste all the output here.

---

### Post by skizeee on 2009-01-09
Hi there

skiz@skizeee:~$ lsusb
Bus 005 Device 006: ID 0d49:7410 Maxtor 
Bus 005 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
skiz@skizeee:~$ 


and for the other...

skiz@skizeee:~$ gksu fdisk -l
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
skiz@skizeee:~$ 


thanks!

---

### Post by sadaruwan12 on 2009-01-09
> **skizeee said:**
> 
skiz@skizeee:~$ gksu fdisk -l
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
skiz@skizeee:~$ 


thanks!

use
```
sudo fdik -l
```

post the out put

---

### Post by sadaruwan12 on 2009-01-09
> **skizeee said:**
> 
skiz@skizeee:~$ gksu fdisk -l
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
skiz@skizeee:~$ 


thanks!

use
```
sudo fdisk -l
```

post the out put

---

### Post by skizeee on 2009-01-09
Hi there

output is:

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58d1ca06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         490     3935893+  83  Linux

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8949

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          31      248976   82  Linux swap / Solaris
/dev/sdb2              32         981     7630875    5  Extended
/dev/sdb5              32         981     7630843+  83  Linux


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09286826

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976762552+   b  W95 FAT32

---

### Post by nothingspecial on 2009-01-09
Skizeee mate, don`t create multiple threads on the same topic. It`s more difficult to help you then.

It appears from what I`ve read that you`ve got a problem. Have you tried other suggestions from your other thread.

Force mount the drive as you were shown then cd into it, note you might have to use sudo in front of some commands.

```
cd /media/disk
``` (or wherever you mounted it)

List all the directories in the drive showing permissions ```
ls -l
```

cd into your music folder and see if the terminal can find your music with ls

The cd command means change directory

ls tells you what`s in the directory your in.

If you don`t understand post back.

---

