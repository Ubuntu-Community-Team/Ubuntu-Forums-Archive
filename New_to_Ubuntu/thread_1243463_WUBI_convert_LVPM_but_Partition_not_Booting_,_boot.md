---
title: "WUBI convert LVPM but Partition not Booting , boot on linux partition and not MBR"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by ozkhalsa on 2009-08-18
Hi Somebody there to help.

I had a perfect cofigured and working Ubuntu install on Win WUBI set up. I used LVPM to transfer to proper Partition. But My GRUB is is lost and only boots windows , Thw WUBI and New Hard install could nto recue despite using Super GRUB disk.

Need script on Terminal to sort this which I am not Good at so Pls help.

Have live CD to Install.

M6400 Dell Precision 2 hardisks.

My device Map is

fd0)    /dev/fd0  OEM dell
(hd0)    /dev/sda  Windows Vista and LInux
(hd1)    /dev/sdb  Windows 7

And Fdisk are here.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40ab005d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       44688   358848512    7  HPFS/NTFS
/dev/sda3           44688       46339    13260800   82  Linux swap / Solaris
/dev/sda4           46342       60801   116149950   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          14      112423+  de  Dell Utility
/dev/sdb2   *          15       19457   156175897+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```


pls help

ozkhalsa

---

### Post by ozkhalsa on 2009-08-18
Loaded the Live CD and the partition for the hard disk install is fully visisble with all files , I can see a **boot **folder but would not like to touch it as do not know the inner working of boot loader grub and  Ubuntu/linux.

---

