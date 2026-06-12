---
title: "External Hard drive mount problem (new)"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by spue on 2009-02-26
I've looked around and seem to have a fairly unique problem.

my external hard drive automounted fine when using a kubuntu 8.04 live cd.
it will not under ubuntu 8.10 (the ver. i want to use)  nothing happens when i plug it in.

"fdisk -l" output does not show the drive and i can't find it anywhere to try manually mounting it. 

BTW, kubuntu 8.10 also will not automount it.

TIA

---

### Post by cariboo on 2009-02-26
Have you tried the drive on another computer to make sure it still works?

Jim

---

### Post by spue on 2009-02-26
yes.. and it works fine under kubuntu 8.04

BTW... it is formatted FAT

---

### Post by kansasnoob on 2009-02-26
Kubuntu includes more tools - it's heavy but it has a lot of stuff installed by default.

In Ubuntu I always install "pmount" either from Synaptic or you can use the terminal:

```
sudo apt-get install pmount
```

Brief explanation of pmount from Synaptic:

> mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

---

### Post by kansasnoob on 2009-02-26
BTW Kubuntu uses kio.........

Lots of kio............

---

### Post by spue on 2009-02-26
tried pmount... still no luck
what is kio?

---

### Post by powder on 2009-02-26
If this is a desktop, try the USB ports on the rear of the computer.

---

### Post by blueridgedog on 2009-02-26
With the device plugged in, can you post:

```
lsusb
```

and 

```
fdisk -l
```

---

### Post by spue on 2009-02-26
spue@spue-laptop:~$ lsusb
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 2116:0320  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


spue@spue-laptop:~$ sudo fdisk -l
[sudo] password for spue: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13d113d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1942    15599083+   7  HPFS/NTFS
/dev/sda2            1943        9729    62549077+   5  Extended
/dev/sda5            1943        9554    61143358+  83  Linux
/dev/sda6            9555        9729     1405656   82  Linux swap / Solaris

---

### Post by blueridgedog on 2009-02-27
You computer dose not see the hard drive.  I suggest you verify that it has power, and try a different USB port.  There is one mystery device:

Bus 001 Device 006: ID 2116:0320

Which may be it.

Can you test the drive on another PC?

---

### Post by spue on 2009-02-27
i have tested it on another computer and it works.
it works great on this computer when i boot a kubuntu 8.04 live cd.
the drive and all cables are fine.

---

### Post by spue on 2009-03-19
still hoping somebody can help me here.

i'll repeat... the drive works fine on other computers AND this computer when running a KUBUNTU 8.04 live session.

doesnt work with ubuntu 8.10 or kubuntu 8.10 (strangely)

thanx for taking some time to read this and hopefully help.

---

### Post by Rielpicon on 2009-03-19
Bus 007 Device 007: ID 059b:0375 Iomega Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 006: ID 0a5c:4503 Broadcom Corp. 
Bus 006 Device 005: ID 0a5c:4502 Broadcom Corp. 
Bus 006 Device 004: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 006 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
gabriel@dell-desktop:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdc
gabriel@dell-desktop:~$

---

### Post by blueridgedog on 2009-03-21
> **spue said:**
> still hoping somebody can help me here.

i'll repeat... the drive works fine on other computers AND this computer when running a KUBUNTU 8.04 live session.

doesnt work with ubuntu 8.10 or kubuntu 8.10 (strangely)

thanx for taking some time to read this and hopefully help.

OK, power up the system without the drive.  Plug it in and then run the command:

```
dmesg
```

Please post the bottom of the output triggered by you plugging the drive in.  We are looking to see what you system makes of the drive.

---

