---
title: "help how to mount my sd ?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by nooor7772000 on 2011-06-15
hi guys 
i have my ubuntu 11.04 in my htc shift and i can not read my sd at all althought i read it in my windows xp side
so what can i do to read it
thanks

---

### Post by wildmanne39 on 2011-06-15
> **nooor7772000 said:**
> hi guys 
i have my ubuntu 11.04 in my htc shift and i can not read my sd at all althought i read it in my windows xp side
so what can i do to read it
thanksHi, when you open file manager you should see it on the left side of the window it is probably listed by size. If it is not there go to dash open disk utility and it should be there, if you see it and it is not mounted mount it from disk utility.

---

### Post by elliotbeken on 2011-06-15
I believe this command will show you if the OS sees the drive, also if it is listed you can see the information needed to manually mount from the terminal if you need to.
> sudo fdisk -l
(-L)

---

### Post by nooor7772000 on 2011-06-15
thanks so much  guys for reply 
but i realy can not find it in file manger
or even disk utility
and i did 

sudo fdisk -l 

Disk /dev/sda: 40.0 GB, 40000536576 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xXXXXXXXXXX

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4862    28812577+   f  W95 Ext'd (LBA)
/dev/sda5            1276        4862    28812546    7  HPFS/NTFS


what shall i do?

---

### Post by wildmanne39 on 2011-06-15
> **nooor7772000 said:**
> thanks so much  guys for reply 
but i realy can not find it in file manger
or even disk utility
and i did 

sudo fdisk -l 

Disk /dev/sda: 40.0 GB, 40000536576 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xXXXXXXXXXX

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4862    28812577+   f  W95 Ext'd (LBA)
/dev/sda5            1276        4862    28812546    7  HPFS/NTFS


what shall i do?
Hi, it look like you did a wubi install is that correct? if so I believe you can see it in your home folder but I am not sure about that, if it is wubi check the wubi mega thread.

---

### Post by sandyd on 2011-06-15
> **nooor7772000 said:**
> thanks so much  guys for reply 
but i realy can not find it in file manger
or even disk utility
and i did 

sudo fdisk -l 

Disk /dev/sda: 40.0 GB, 40000536576 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xXXXXXXXXXX

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4862    28812577+   f  W95 Ext'd (LBA)
/dev/sda5            1276        4862    28812546    7  HPFS/NTFS


what shall i do?

Even though its wubi, it should show.

Post output of
```

sudo lspci
```

---

### Post by nooor7772000 on 2011-06-17
yea i did wubi install ,and nothing in home folder
second i did this command in shell
sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:06.0 SD Host controller: C-guys, Inc. CG200 Dual SD/SDIO Host controller device (rev 09)

then what

---

