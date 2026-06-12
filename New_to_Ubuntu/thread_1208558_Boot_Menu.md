---
title: "Boot Menu"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-07-09
I'm wondering how I could get a boot menu for XP and Jaunty w/o over-writing the Master Boot on my XP? 

I have two HDD in separate bays in my T30. I've been doing a little reading and seems I may need to make changes to Grub??? Here's a little light on my current HDD setups:

[CENTER]**fdisk -l**[/CENTER]

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa266a266

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10107    76408888+   7  HPFS/NTFS
/dev/sda2           10108       10337     1738800   1c  Hidden W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dae8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2315        4864    20482875    b  W95 FAT32
/dev/sdb2               1        2314    18587173+   5  Extended
/dev/sdb5               1        2212    17767827   83  Linux
/dev/sdb6            2213        2314      819283+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

[CENTER]**Menu.lst**[/CENTER]

```
title		Ubuntu 9.04, kernel 2.6.28-13-generic 
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic 
quiet 

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) 
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro  single 
initrd		/boot/initrd.img-2.6.28-13-generic 

title		Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic 
quiet 

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) 
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro  single 
initrd		/boot/initrd.img-2.6.28-11-generic 

title		Ubuntu 9.04, memtest86+ 
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I REALLY don't want Grub to overwrite my MBR in XP. I have a recovery partition I want to keep! I've already NOOBINGLY overwrote the MBR before. I didn't have the recovery disks so I had to order the RnR disks. Getting my settings back to how I want it after a wipe and reinstall is no fun!!!

	](*,)

Currently I've just been using my F1 BIOS setup to boot into whichever OS I want to use. It would just be more convenient for me to turn my laptop on and have a menu to choose OS from. I'm pretty much still NOOBY so if anyone has any suggestions please submit! Thanks :)

---

### Post by tarps87 on 2009-07-09
After ### END DEBIAN AUTOMAGIC KERNELS LIST

Add the following

title           Windows XP
rootnoverify    (hd0,0)
makeactive
chainloader     +1

I believe this should work with your current set up, if not try (hd1,0)

---

### Post by superprash2003 on 2009-07-09
or you could boot the ubuntu live cd and run grub again and it should look for all OS and create a new boot menu.[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

