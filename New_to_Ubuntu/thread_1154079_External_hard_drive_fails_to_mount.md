---
title: "External hard drive fails to mount"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by kapi on 2009-05-09
Hope someone can shed some light,

have a new external 500GB hard drive, used it a few times and it seemed ok. Went to use it recently and got

$MFTMirror Error does not match MFT record(0)

can anyone please help. I have tried the drive on a windows machine and the thing loads ok. on Ubuntu I get this message

---

### Post by StOoZ on 2009-05-09
does linux recognizes it?
what is the output of :
> sudo fdisk -l

---

### Post by kapi on 2009-05-09
Thanks for replying. The output is as follows:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37793778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x454c507c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

---

### Post by keithweddell on 2009-05-09
This looks like the same problem: [Link]("http://ubuntuforums.org/archive/index.php/t-656025.html")

---

### Post by kapi on 2009-05-10
no sorry the volume failed to mount.keeps telling me to run chkdsk

---

