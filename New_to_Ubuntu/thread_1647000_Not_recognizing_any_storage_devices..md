---
title: "Not recognizing any storage devices."
date: 2010-12-16
forum: New to Ubuntu
---

### Post by ramoj02 on 2010-12-16
My Ubuntu 10.10 is not recognizing my USB thumbdrive. But I have USB devices, like USB mouse, webcam, and wireless card, and they're all working fine when connected to my netbook. And I know the problem is not on my thumbdrive because I've used three different kinds, and none of them work. They all light up, indicating that there's power. But my netbook just won't recognize them, it won't show the connected thumdrive on "Computer", or on my desktop.

Also, I tried putting an SD card in the card-reader slot, and it won't recognize it also. So, I think my netbook (Acer Aspire One) is not recognizing any memory/media storage devices.

Any help would be greatly appreciated. :)

---

### Post by dpwilson on 2010-12-16
If you go to system-administration-users&groups, then click advanced settings- is access external storage devices checked?

---

### Post by dpwilson on 2010-12-16
another thing to try, in terminal type in
```
gconf-editor
```

 go to apps-nautilus-preferences

make sure media-automount is set to true (checked)

---

### Post by ramoj02 on 2010-12-16
> **dpwilson said:**
> another thing to try, in terminal type in
```
gconf-editor
```

 go to apps-nautilus-preferences

make sure media-automount is set to true (checked)

> **dpwilson said:**
> If you go to system-administration-users&groups, then click advanced settings- is access external storage devices checked?

Both checked.

---

### Post by sandyd on 2010-12-16
wait. do you have everything plugged in while testing the USB drive?
The USB drive may have enough power to light up, but not enough power to start functioning.

post output of
```

fdisk -l
lsusb
```
while device is plugged in btw.

---

### Post by ramoj02 on 2010-12-16
> **sandyd said:**
> wait. do you have everything plugged in while testing the USB drive?
The USB drive may have enough power to light up, but not enough power to start functioning.

post output of
```

fdisk -l
lsusb
```
while device is plugged in btw.

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by ramoj02 on 2010-12-16
> **sandyd said:**
> wait. do you have everything plugged in while testing the USB drive?
The USB drive may have enough power to light up, but not enough power to start functioning.

post output of
```

fdisk -l
lsusb
```
while device is plugged in btw.

Sorry for not posting the full output.

fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000501db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19076   153219072   83  Linux
/dev/sda2           19076       19458     3068929    5  Extended
/dev/sda5           19076       19458     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 4012 MB, 4012900352 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc5cb6e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3918816+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(486, 254, 63) logical=(487, 222, 55)

```

lsusb:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

*Note: I ran the commands while the thumbdrive is plugged in.*

---

### Post by salemboot on 2010-12-16
cat /etc/group | grep plugdev

See if your user account is associated with that group.

---

### Post by ramoj02 on 2010-12-17
> **salemboot said:**
> cat /etc/group | grep plugdev

See if your user account is associated with that group.

```
plugdev:x:46:mangcool
```

*My username is "mangcool".*

---

### Post by ramoj02 on 2010-12-17
Any ideas guys? Sorry for not being patient, but I really need this thing fixed. :/

Thanks!

---

### Post by sandyd on 2010-12-17
> **ramoj02 said:**
> Sorry for not posting the full output.

fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000501db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19076   153219072   83  Linux
/dev/sda2           19076       19458     3068929    5  Extended
/dev/sda5           19076       19458     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 4012 MB, 4012900352 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc5cb6e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3918816+   b  W95 FAT32
[B]Partition 1 has different physical/logical endings:
     phys=(486, 254, 63) logical=(487, 222, 55)[/B]

```lsusb:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```*Note: I ran the commands while the thumbdrive is plugged in.*
weird.
but w/e
```

sudo mkdir /mnt/usbdrive
sudo mount /dev/sdb1 -t vfat /mnt/usbdrive
```

---

### Post by marc.m on 2011-03-02
[Another thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1657581") recommended

```
sudo apt-get install usbmount
```

worked for me. :KS

---

