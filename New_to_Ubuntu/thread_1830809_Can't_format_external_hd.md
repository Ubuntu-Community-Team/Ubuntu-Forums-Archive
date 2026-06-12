---
title: "Can't format external hd"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by mutthew on 2011-08-22
I just bought a LaCie 500GB rugged external hd, and want to format it for linux.   :confused:

Things I have tried:

Disk Utility --> Format Drive
Shows me the LaCie disk, but gives me: "Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No such device or address"

Disk Utility --> Format volume
Shows me the LaCie disk, but gives me: "Error creating file system: helper exited with exit code 1: cannot open /dev/sdb: No such device or address"

Gparted
Only shows me the partitions on my computer, and refresh devices still doesn't find the LaCie hd.

Please help, I have sworn off Windows and want to be able to do this in Linux.  I am still very new to this though, so please be specific in any helping instructions.  Thanks!

If it helps, I am running a freshly updated Ubuntu Natty Narwhal on a Lenovo T61.

---

### Post by seawolf167 on 2011-08-22
When running GParted, after you hit 'refresh', you don't have the option under the top-right drop down menu to select your external hard drive?

What is the output of the follow commands (with the drive plugged in):
```
sudo fdisk -l
sudo blkid
```

---

### Post by mutthew on 2011-08-22
That's right, in Gparted I don't have the option to select it under drives after I hit refresh.  It just doesn't show up.

Thist is the output of
sudo fdisk -l sudo blkid 


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83db52c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29296875    7  HPFS/NTFS
/dev/sda2            3648       30402   214899713    5  Extended
/dev/sda5            3648        5472    14647296   83  Linux
/dev/sda6            5472        5715     1951744   82  Linux swap / Solaris
/dev/sda7            5715       30402   198298624   83  Linux

---

### Post by seawolf167 on 2011-08-22
And your drive is plugged in? It doesn't look like it is being recognized... 

One more test, please run the following command

```
sudo lshw -C disk
```

and post the output

---

### Post by mutthew on 2011-08-22
I do have it plugged in, but it's brand new... so I'm not sure that it works.

sudo lshw -C disk gives me:

  *-disk                  
       description: ATA Disk
       product: SAMSUNG HM251HI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 2AJ1
       serial: S2EGJDQZ601609
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=83db52c5
  *-cdrom
       description: DVD reader
       product: DVD/CDRW UJDA775
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CB03
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-disk UNCLAIMED
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@8:0.0.0



another command I found,  cat /proc/scsi/scsi, seems to indicate it is recognized somewhere.  it gives me:
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: SAMSUNG HM251HI  Rev: 2AJ1
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: MATSHITA Model: DVD/CDRW UJDA775 Rev: CB03
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi8 Channel: 00 Id: 00 Lun: 00
  Vendor: LaCie    Model: Rugged FW USB3   Rev: 1081
  Type:   Direct-Access                    ANSI  SCSI revision: 04

---

### Post by seawolf167 on 2011-08-22
Does you model have a separate power cable that you need to plug in? Or a power switch you can turn on?

---

### Post by mutthew on 2011-08-22
No, no power switch or power cable.  I have powered other external hd's from my usb port before though, so it should work.

---

### Post by mutthew on 2011-08-22
ended up returning the hd.  bummer :(

---

