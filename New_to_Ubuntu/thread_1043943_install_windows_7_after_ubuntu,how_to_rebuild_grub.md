---
title: "install windows 7 after ubuntu,how to rebuild grub"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by biaodianfu on 2009-01-19
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d979d97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            2551        5101    20490876   83  Linux
/dev/sda6            5102        5363     2104483+  82  Linux swap / Solaris
/dev/sda7            5364        7914    20490876    b  W95 FAT32
/dev/sda8            7915       10465    20490876    b  W95 FAT32
/dev/sda9           10466       13016    20490876    b  W95 FAT32
/dev/sda10          13017       15567    20490876    b  W95 FAT32
/dev/sda11  *       15568       18118    20490876   af  Unknown
/dev/sda12          18119       19457    10755486    7  HPFS/NTFS
```

---

### Post by Sullr on 2009-01-19
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

[original link ]("http://ubuntuforums.org/archive/index.php/t-24113.html")

---

### Post by biaodianfu on 2009-01-19
> **Sullr said:**
> 1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

[original link ]("http://ubuntuforums.org/archive/index.php/t-24113.html")
it can not work

---

### Post by Sullr on 2009-01-19
Explain??

I just used that exact method after installing 7 5 minutes ago!

---

