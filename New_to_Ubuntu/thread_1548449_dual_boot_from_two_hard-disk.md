---
title: "dual boot from two hard-disk"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by godsmAsh on 2010-08-08
hi, 
 i have 2 hd.  1 idle and 1 sata.  the idle has ubuntu installed and sata has two partition 1 having Win 7 and the other  contains no OS. 

the  problems are as follows: 

1- when i boot i don't see the menu to select the appropriate OS.

2- when i'm in ubuntu, i don't see the Win 7 partition. 

can anyone please help me.

---

### Post by ikt on 2010-08-08
> **godsmAsh said:**
> hi, 
 i have 2 hd.  1 idle and 1 sata.  the idle has ubuntu installed and sata has two partition 1 having Win 7 and the other  contains no OS. 

ide: ubuntu
sata: win7 + no os

> **godsmAsh said:**
> 
the  problems are as follows: 

1- when i boot i don't see the menu to select the appropriate OS.

2- when i'm in ubuntu, i don't see the Win 7 partition. 

can anyone please help me.

I assume you are booting directly into ubuntu, if both are plugged in, head to the terminal and type

"sudo update-grub" without the "".

This will cause Grub2 to search out for windows and add it to the list.

> Automated searches for other operating systems, such as Windows, whenever update-grub is executed.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by godsmAsh on 2010-08-08
i've tried "sudo update-grub" but it says

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done


no win7

---

### Post by QIII on 2010-08-08
Could you type 

```
sudo fdisk -l
```in the terminal and post the results?

(That's a small "ell", not a "one")

---

### Post by godsmAsh on 2010-08-09
now i'm being able to mount the win7 partition.  but another prob arises. when it boot, it goes directly to ubuntu. 

----------------------------
Disk /dev/sda: 164.7 GB, 164696555520 bytes
78 heads, 36 sectors/track, 114555 cylinders
Units = cylinders of 2808 * 512 = 1437696 bytes
Disk identifier: 0x00a0009f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1875     2630656   82  Linux swap / Solaris
/dev/sda2            1876      114556   158202880+   5  Extended
/dev/sda5            1876      114556   158202880   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd64364ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       60802   488282112    7  HPFS/NTFS

---

### Post by ikt on 2010-08-09
> **godsmAsh said:**
> now i'm being able to mount the win7 partition.  but another prob arises. when it boot, it goes directly to ubuntu. 

----------------------------
Disk /dev/sda: 164.7 GB, 164696555520 bytes
78 heads, 36 sectors/track, 114555 cylinders
Units = cylinders of 2808 * 512 = 1437696 bytes
Disk identifier: 0x00a0009f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1875     2630656   82  Linux swap / Solaris
/dev/sda2            1876      114556   158202880+   5  Extended
/dev/sda5            1876      114556   158202880   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd64364ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       60802   488282112    7  HPFS/NTFS

If you run the update-grub command with the windows drive mounted does it find it?

---

### Post by john newbuntu on 2010-08-09
I suspect a problem with the boot sector of win 7 in your second drive.  You will most likely require repairing your win7 boot sector as detailed in:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Before doing anything though, your fdisk output shows 2 partitions on the second drive - one 100MB and the other 488GB.  However, the boot flag is on the 100MB one which is odd.

Prior to repairing your boot sector, download and run the boot info script  [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)  Follow the instructions on this page very carefully.  Post the output using code tags so that some of us can offer a better fix.

---

### Post by godsmAsh on 2010-08-10
a simple  update-grub did work.. thanks

---

