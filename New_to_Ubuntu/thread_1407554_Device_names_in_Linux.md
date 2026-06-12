---
title: "Device names in Linux"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by SteelCore on 2010-02-15
AFAIK Linux names ATA drives (IDE) using the hdx convention where x could be a,b,c or d
Same goes for SATA and SCSI drives. They get the sdx names.

My Ubuntu has 4 hard disks; 2 ATA and 2 SATA. When I installed them I expected:
/dev/hda
/dev/hdb
/dev/sda
/dev/sdb

instead I got
/dev/sda
/dev/sdb
/dev/sdc
/dev/sdd
so I assume my naming rules are all wrong. so what is the difference between sd and hd?
Thanks

---

### Post by luckydeveloper on 2010-02-15
[http://superuser.com/questions/81034/linux-disk-naming-convention](http://superuser.com/questions/81034/linux-disk-naming-convention)

---

### Post by audiomick on 2010-02-15
The "hdx" names stopped being used a while back. I don't know exactly why, but now all drives turn up as "sdx", at least as far as I know.

The numbering scheme is the same, with a couple of things to note:
1 to 4 is reserved for primary partitions. Logical partitions always start at 5, so if you have one primary and one extended with 2 logicals inside it, you will have
sda1 - the primary
sda2 - the extended
sda5 - the first logical
sda6 - the second logical

The numbers aren't necessarily  assigned according to the position on the drive. If you do a few successive changes to the partition table, you can end up with lower numbers towards the end of the drive. See mine:
```
mick@ubuntu-desktop:~$ sudo fdisk -l
[sudo] password for mick: 

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
/dev/sdb1               1       60424   485355748+  83  Linux
/dev/sdb2           60425       60801     3028252+  82  Linux Swap / Solaris

```"Erweiterte" means "extended". You will notice that sda5 is physically after sda6 and sda7

---

### Post by sisco311 on 2010-02-15
> **audiomick said:**
> The "hdx" names stopped being used a while back. I don't know exactly why, but now all drives turn up as "sdx", at least as far as I know.





The IDE driver in the Linux kernel has been functionally replaced by the PATA driver which uses the sdx naming convention.

[http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce](http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce)

---

