---
title: "$/dev/mapper/sda1 not identified as an existing physical volume"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by krajschmitz on 2009-07-11
I'm running Ubuntu 9.04 Server w/o gui.  
My original is
 $sudo vgextend volumegroup /dev/sda1
 $/dev/mapper/sda1 not identified as an existing physical volume
 $Unable to add physical volume '/dev/mapper/sda1' to volume group 'volumegroup'.

 $sudo vgextend --version
 $LVM version:     2.02.39 (2008-06-27)
 $Library version: 1.02.27 (2008-06-25)
 $Driver version:  4.14.0

If it helps
 $sudo fdisk -l
 $Disk /dev/sda: 80.0 GB, 80054059008 bytes
 $255 heads, 63 sectors/track, 9732 cylinders
 $Units = cylinders of 16065 * 512 = 8225280 bytes
 $Disk identifier: 0xa5ebf8b4
 $
 $   Device Boot      Start         End      Blocks   Id  System
 $/dev/sda1   *           1        9732    78172258+  83  Linux
 $
 $Disk /dev/sdb: 80.0 GB, 80054059008 bytes
 $255 heads, 63 sectors/track, 9732 cylinders
 $Units = cylinders of 16065 * 512 = 8225280 bytes
 $Disk identifier: 0x00000001
 $
 $   Device Boot      Start         End      Blocks   Id  System
 $/dev/sdb1               1        9702    77931283+  83  Linux
 $/dev/sdb2            9703        9732      240975    5  Extended
 $/dev/sdb5            9703        9732      240943+  83  Linux
Thanks

---

### Post by Najand on 2009-07-11
What exactly do you want to do?

---

### Post by krajschmitz on 2009-07-12
I wanted to extend my volume group to include my second hard drive

---

### Post by krajschmitz on 2009-07-12
I solved the problem.

---

### Post by low351 on 2009-10-29
I solved the problem!?! :( that's it? no explanation of how.

I'll submit that you probably forgot to do a _pvcreate_ on the device first.

I had the exact same problem and found this thread but figured out what was wrong... ;)

---

