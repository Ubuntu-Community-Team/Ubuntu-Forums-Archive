---
title: "can't mount or format usb drive"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by alqershi on 2009-08-14
Hi everybody, I'm a windows junky who converted recently to Linux. I got fed up with windows crap and decided to be a linux guy. So far everything is great. Yesterday, i formated my usb using gparted and before the format is completed the power got disconnected from my pc :(. after restarting the machine, the pc can't mount the usb drive anymore. I can't format the usb because gparted CAN'T FIND IT. When I click on mu computer i can see the usb device but when i click on the usb, it says unable to mount location No media in the drive. I unpluged the usb and plug it again and i run the command ```
dmesg | tail
```the output was 
```
[  219.475400] usb 2-5: USB disconnect, address 3
[  280.020209] usb 2-5: new high speed USB device using ehci_hcd and address 5
[  280.160272] usb 2-5: configuration #1 chosen from 1 choice
[  280.160857] scsi5 : SCSI emulation for USB Mass Storage devices
[  280.161806] usb-storage: device found at 5
[  280.161811] usb-storage: waiting for device to settle before scanning
[  285.160620] usb-storage: device scan complete
[  285.162293] scsi 5:0:0:0: Direct-Access              USB MEMORY BAR   1000 PQ: 0 ANSI: 0 CCS
[  285.166215] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  285.166339] sd 5:0:0:0: Attached scsi generic sg2 type 0

```when I opened /etc/fstab the output was
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2f862b71-99e3-4372-9ab3-d377275adb98 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ffa3ee8a-bc8b-40c5-9a55-2c3c13f05b8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```I run the command fdisk -l and the output is 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2379979

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19088   153324328+  83  Linux
/dev/sda2           19089       19457     2963992+   5  Extended
/dev/sda5           19089       19457     2963961   82  Linux swap / Solaris

```Please help me out. I don't know what to do anymore. I did alot of research and can't find a solution so far.

Thank you

---

### Post by LewRockwell on 2009-08-14
[http://ubuntuforums.org/showthread.php?t=66731](http://ubuntuforums.org/showthread.php?t=66731)

[http://ubuntuforums.org/showthread.php?t=674002](http://ubuntuforums.org/showthread.php?t=674002)

.

---

### Post by alqershi on 2009-08-15
Hi LewRockwell,

I tried the steps described in the above urls, but I always get the same answer
```
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No medium found while trying to open /dev/sdb

```

I'm going crazy :confused:

---

### Post by Bachstelze on 2009-08-15
Are you sure your USB key works properly? If it isn't detected by [font=monospace]sudo fdisk -l[/font], the only reason I can see is a hardware problem.

---

### Post by arjuntank on 2009-08-15
this happened to a lot of my friends. if u remove ur usb drive while booting (during bios POST) or power gets off, which is ur case, it wont work afterwards :(

---

### Post by LewRockwell on 2009-08-15
slow burn the latest Parted Magic LiveCD, boot it up and attempt to run the secure erase function on THAT DRIVE(make sure you don't erase the wrong drive)

AGAIN, MAKE SURE YOU DO NOT ERASE THE WRONG PARTITION OR THE WRONG DRIVE!

SECURE ERASE IS JUST THAT...SECURE...UNRECOVERABLE...COMPLETE DATA DESTRUCTION!

[http://partedmagic.com/](http://partedmagic.com/)

.

---

