---
title: "USB device not being detected / mounted"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Logan 1229 on 2009-05-17
Running 9.04 

Tried connecting a USB mp3 player/memory device however doesn't seem to detect it. All other USB devices I have auto-mount as soon as plugged in. Any ideas?

dsmeg | tail -10 :

[ 4057.047972] sd 16:0:0:0: [sde] 7860224 512-byte hardware sectors: (4.02 GB/3.74 GiB)
[ 4057.047976] sd 16:0:0:0: [sde] Assuming Write Enabled
[ 4057.047977] sd 16:0:0:0: [sde] Assuming drive cache: write through
[ 4057.049449] sd 16:0:0:0: [sde] 7860224 512-byte hardware sectors: (4.02 GB/3.74 GiB)
[ 4057.049452] sd 16:0:0:0: [sde] Assuming Write Enabled
[ 4057.049454] sd 16:0:0:0: [sde] Assuming drive cache: write through
[ 4057.049459]  sde:
[ 4057.051189] sd 16:0:0:0: [sde] Attached SCSI removable disk
[ 4057.051252] sd 16:0:0:0: Attached scsi generic sg5 type 0
[ 4057.051948] sd 16:0:0:1: [sdf] Very big device. Trying to use READ CAPACITY(16).

lsusb :

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by MontelEdwards on 2009-05-21
Hello could you please run ```
sudo fdisk -l 
```
and tell me the output.
thanx

---

### Post by Logan 1229 on 2009-05-24
> **MontelEdwards said:**
> Hello could you please run ```
sudo fdisk -l 
```
and tell me the output.
thanx

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bdfe2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e142

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000563be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005665f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

---

### Post by MontelEdwards on 2009-05-24
Ok, thanks for that.

I really cannot tell which one is your MP3 player
BUT
let's do ```
sudo mkdir /media/mp3

```and thennn
```
sudo mount /dev/sdf [FONT=monospace]/media/mp3[/FONT]
```

---

### Post by collinp on 2009-05-24
First, lets run "lsusb" and paste the output here.

---

### Post by Logan 1229 on 2009-06-22
> **Hellow said:**
> First, lets run "lsusb" and paste the output here.

Sorry for delay folks; renovations & vacations before computer trouble shooting! & then the upgrade to 9.04 caused sudden sound issues, with a topping of pooched mouse to make life interesting... new mouse & dealing with sound via other folks similiar threads. So, 

here's the lsusb (with device plugged in):

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

all usb ports tested & working (plugged a working, detected device into).

---

### Post by Sef on 2009-06-22
1) What's the make and model of your device?

2) If plugged into another machine, is it detected?

---

### Post by Logan 1229 on 2009-06-22
> **MontelEdwards said:**
> Ok, thanks for that.

I really cannot tell which one is your MP3 player
BUT
let's do ```
sudo mkdir /media/mp3

```and thennn
```
sudo mount /dev/sdf [FONT=monospace]/media/mp3[/FONT]
```

Not 100% sure why you wanted me to create & mount this directory but it didn't work.  All devices sda, sdb, sdc, sdd are HDs which are all working properly.

Further ideas?

---

### Post by Logan 1229 on 2009-06-22
> **Sef said:**
> 1) What's the make and model of your device?

2) If plugged into another machine, is it detected?

not a known brand/model (no noticeable brand on it); supposed to be plug a play; works with windows (sadly I admit)

---

