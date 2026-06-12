---
title: "My Newer Technology usb harddrive isn't mounting on ibex"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by luckyd on 2009-02-13
I have tried a lot of different things to get this hard drive to mount. The reason why I keep trying is because I know it did on feisty. I am pretty sure that the harddrive is formated to fat32. Nothing turned up when I ran  dmesg | grep sda
 and sudo fdisk -l
returns
> Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  de  Dell Utility
/dev/sda2               7         268     2104515    b  W95 FAT32
/dev/sda3             269         293      200812+  83  Linux
/dev/sda4             294       30394   241786282+   f  W95 Ext'd (LBA)
/dev/sda5           27784       30394    20972826   83  Linux
/dev/sda6             294       27409   217809207   83  Linux
/dev/sda7           27410       27783     3004123+  82  Linux swap / Solaris

Any ideas?

---

### Post by jerome1232 on 2009-02-13
With it plugged in what's the output of lsusb, it looks like according to the output of fdisk -l you system isn't picking up the second disc.

Have you tried different usb ports maybe the one your trying to use is fried, or if your going through a usb hub try and connect it directly to one of the machines ports.

```
lsusb
```

---

### Post by luckyd on 2009-02-13
Well I'm not sure what it means, but lsusb gives
> Bus 007 Device 011: ID 0dc4:0073 Macpower Peripherals, Ltd 
Bus 007 Device 010: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 2222:2520 MacAlly 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I believe it is the Macpower Periphals, Ltd

---

### Post by luckyd on 2009-02-13
heres the fix [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983)

---

### Post by luckyd on 2009-02-13
the thread is solved

---

