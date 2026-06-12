---
title: "DVD-RW not working"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by mern1 on 2009-01-06
Just recently installed 8.10 and am unable to get my dvdrw drive to work. With a CD in the drive it says it cannot be mounted (no media in the drive). Any help would be greatly appreciated as I don't really have a clue what I'm doing. Thanks

Results from lshw -C disk:
```


*-cdrom:0               
       description: DVD-RAM writer
       product: DVDRW SHM-165H6S
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HS0D
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-cdrom:1
       description: CD-R/CD-RW writer
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw
       configuration: status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@8:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANK1507472
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=52685268
  *-disk:1
       description: ATA Disk
       product: WDC WD1001FALS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@9:0.0.0
       logical name: /dev/sdb
       version: 05.0
       serial: WD-WMATV0374195
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5e378cc5
```

fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ed815082-ef9c-4e93-90a4-409f4f584987 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4908b1d5-ef40-4220-bdad-64ef568f9ce3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1 
UUID=2C6827E96827B08E /media/Shared   ntfs-3g  ro,auto,user,fmask=0111,dmask=0000 0 0
```

---

### Post by Shazaam on 2009-01-06
I have 2, a Lite-On and a Sony and this is what shows in fstab (one listing for both)...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab /    ext3 relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=09629083-8b5c-4e52-8c8e-36580fc338e0 none      swap  sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
and they both work fine. lshw -C disk...
```
*-disk                  
       description: ATA Disk
       product: WDC WD3200JD-00K
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 08.0
       serial: WD-WCAMR2240274
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00047d37
 *-disk
       description: ATA Disk
       product: WDC WD800JB-00ET
       vendor: Western Digital
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 77.0
       serial: WD-WCAHL3250889
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000096f6
 *-cdrom:0
       description: DVD reader
       product: DVD C  LH52C1P
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 6L14
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
 *-cdrom:1
       description: DVD writer
       product: DVD RW DRU-720A
       vendor: SONY
       physical id: 0.1.0
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: JY08
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

```
Maybe try commenting out (one at a time) one of the drives in fstab? The Sony always shows as the default drive unless I specify otherwise.

---

### Post by mern1 on 2009-01-07
That didn't work.  No matter what I do with my CD-RW drive (list it in fstab or not) it works perfectly.  However, nothing I do will get my DVD-RW to work.  Any other suggestions?

---

