---
title: "problem after deleting partition"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by agmath on 2010-12-03
I had dual boot, one windows 7 (64bit), and ubuntu 10.10 (32 bit). For uninstalling ubuntu, I by mistake, reformatted the ubuntu partition to ntfs. After that when I rebooted the machine, it says ```
error: unknown filesystem.
grub rescue>
```In order to fix it, I followed the following procedure: after booting up from the first of my four windows 7 cds, I went on to system recovery, and in command prompt, typed ```
Bootrec /RebuildBcd
``` and it was successful, as it said. However, after removing the cd, when i rebooted the machine, same trouble endured.

As a second attempt, I tried to follow the instructions given in the following page: [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

But, as I have already mentioned, i have four cds, and i inserted only the first one; and after the 7th step in the instruction (above page), it did NOT show the bootsect.exe at all!

Kindly help me out.

Best, 
Anjan

---

### Post by Quackers on 2010-12-03
Try bootrec.exe /fixmbr

---

### Post by agmath on 2010-12-03
Thank you.It started working.

---

### Post by jplo on 2010-12-03
> **agmath said:**
> Thank you.It started working.

This error occurred because GRUB is installed on the same partition as Ubuntu. Without running fixmbr, your computer will have attempted to start GRUB, which did not exist on the partition. :confused:

---

