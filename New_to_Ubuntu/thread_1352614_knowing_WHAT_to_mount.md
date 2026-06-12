---
title: "knowing WHAT to mount"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by rebeltaz on 2009-12-11
I admit I am relatively new to Linux, but I understand that in order for a hard drive to be accessible under Linux, it must first be mounted. I understand the mount command. What I don't understand is how do I know what the designation is of the drive that I want to mount. I know that the master hard drive that Linux is installed and run from is /dev/sda and I assume that the separate partitions would be /dev/sda1, /dev/sda5 etc. So if I were to add a second hard drive, would it then become /dev/sdb or something totally different? And if I added a third? And what about something like a compact flash microdrive? Where does that come in? 

I have been reading all over the internet and I have two books totaling about 1000 pages each that I have read through and I cannot find an answer to this question - unless I am just overlooking it. 

Thanks....

---

### Post by sandyd on 2009-12-11
> **rebeltaz said:**
> I admit I am relatively new to Linux, but I understand that in order for a hard drive to be accessible under Linux, it must first be mounted. I understand the mount command. What I don't understand is how do I know what the designation is of the drive that I want to mount. I know that the master hard drive that Linux is installed and run from is /dev/sda and I assume that the separate partitions would be /dev/sda1, /dev/sda5 etc. So if I were to add a second hard drive, would it then become /dev/sdb or something totally different? And if I added a third? And what about something like a compact flash microdrive? Where does that come in? 

I have been reading all over the internet and I have two books totaling about 1000 pages each that I have read through and I cannot find an answer to this question - unless I am just overlooking it. 

Thanks....
attach the device and run
```

sudo fdisk -l

```

---

### Post by dhysk on 2009-12-11
if you don't know how you're machine is partitioned you may want to run fdisk command first, attache the drive then do it again.  Whatever changes is the new device.

---

### Post by audiomick on 2009-12-11
according to the linux disc / partition naming system, the second drive will be sdb, the third sdc and so on.

the primary partitions of a disc, of which there can be four, are sda1, sda2, sda3 and sda4. Or, on the second disc, sdb1, sdb2 and so on.

If you make one primary and one extended with 2 logical partitions in it on your third disc, you will have sdc1, sdc5, sdc6, and sdc7. This is because number 1 - 4 is reserved for primary partitions, and logical partitions are always numbered upwards of five, even when there are less than 4 primary.
It gets confusing when you start shuffling logical partitions, because the next available number is issued, regardless of whether previous numbers are still there, and regardless of the physical order on the disc.

Mine looks like this:
```
Platte /dev/sda: 80.0 GByte, 80026361856 Byte
255 Köpfe, 63 Sektoren/Spuren, 9729 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xc3f8aac4

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            3649        9729    48845632+   5  Erweiterte
/dev/sda3            1825        3648    14651280   83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux Swap / Solaris
/dev/sda6            3649        5593    15623149+  83  Linux
/dev/sda7            5594        9327    29993323+  83  Linux

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x63eba0e6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1       60424   485355748+  83  Linux
/dev/sdb2           60425       60801     3028252+  82  Linux Swap / Solaris

```

"erweitert" is german for extended.
sda2 is an extended, containg sda 5,6,7

sda one is the / of my main install. There is a second install in the logical partitions.

sdb1 is my /home on the main install.

There are 2 swap partitions because I read somewhere that dividing your swap space over two discs can bring a speed increase. Since I practically never see any swap usage, that probably only made things overly complicated.

---

### Post by rebeltaz on 2009-12-11
Ok.. I think I get it now.. Thank you all for your help. Still trying to shake all the bad MS habits I've picked up along the way! ](*,)

---

