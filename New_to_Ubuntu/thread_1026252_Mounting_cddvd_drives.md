---
title: "Mounting cd/dvd drives"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by cnaqe1 on 2008-12-30
I cannot mount my cd and dvd drive manually.  The drives will mount when i put a dvd movie or cd in, but they won't read blank disc.  I will give the information about the drives.

gksu gedit /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=340d426e-56e2-422b-b617-77fcac43770d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=110ac2b9-496b-4aa1-9132-be855efa844e none            swap    sw              0       0
/dev/scd1       /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1 udf,
iso9660 user,noauto,exec,utf8 0       0

sudo lshw -C disk:

 *-disk:0                
       description: ATA Disk
       product: WDC WD205BA
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 16.1
       serial: WD-WM9491340048
       size: 19GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000675f
  *-disk:1
       description: ATA Disk
       product: WDC WD3200AAJB-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 00.0
       serial: WD-WCARW6212097
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00005d9b
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: CD-RW  CW-7585
       vendor: MATSHITA
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.04
       serial: [MATSHITACD-RW  CW-7585  1.040
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD reader
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio dvd
       configuration: status=nodisc

Note:  While I was gathering the information there is a blank dvd disc in the dvd drive.  Can anyone help me?

---

### Post by hansdown on 2008-12-30
Hi cnaqe1.

You need to keep in mind that media disks are either + or - .
Your drive seems to handle - disks.

---

### Post by mc4man on 2008-12-30
> description: DVD reader

It actually appears it's just a reader, not a writer

---

