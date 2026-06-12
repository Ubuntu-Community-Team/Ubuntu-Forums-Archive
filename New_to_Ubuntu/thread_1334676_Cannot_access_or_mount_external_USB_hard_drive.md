---
title: "Cannot access or mount external USB hard drive"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by SuaSwe on 2009-11-22
Hi guys!

Just bought myself an external HDD (LG XD2 v1.1) and whilst it is recognised in fdisk, I cannot access it in Nautilus or mount it.

Output of fdisk -l:

```

root@home:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1219     9791586   83  Linux
/dev/sda2            1220        9729    68356575    5  Extended
/dev/sda5            1220        1286      538146   82  Linux swap / Solaris
/dev/sda6            1287        9729    67818366   83  Linux

Disk /dev/sdb: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc79b4a34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

```

Output of dmesg:

```

<omitted>
[36076.896059] usb 1-1: new high speed USB device using ehci_hcd and address 4
[36077.056306] usb 1-1: configuration #1 chosen from 1 choice
[36077.279098] Initializing USB Mass Storage driver...
[36077.281024] scsi2 : SCSI emulation for USB Mass Storage devices
[36077.281327] usbcore: registered new interface driver usb-storage
[36077.281332] USB Mass Storage support registered.
[36077.285070] usb-storage: device found at 4
[36077.285075] usb-storage: waiting for device to settle before scanning
[36082.288963] usb-storage: device scan complete
[36082.289486] scsi 2:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[36082.328222] sd 2:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[36082.339493] sd 2:0:0:0: [sdb] READ CAPACITY(16) failed
[36082.339500] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[36082.339506] sd 2:0:0:0: [sdb] Use 0xffffffff as device size
[36082.339513] sd 2:0:0:0: [sdb] 4294967296 512-byte hardware sectors: (2.19 TB/2.00 TiB)
[36082.341747] sd 2:0:0:0: [sdb] Write Protect is off
[36082.341752] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[36082.341756] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[36082.342527] sd 2:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[36082.346861] sd 2:0:0:0: [sdb] READ CAPACITY(16) failed
[36082.346867] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[36082.346872] sd 2:0:0:0: [sdb] Use 0xffffffff as device size
[36082.346881] sd 2:0:0:0: [sdb] 4294967296 512-byte hardware sectors: (2.19 TB/2.00 TiB)
[36082.347726] sd 2:0:0:0: [sdb] Write Protect is off
[36082.347729] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[36082.347732] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[36082.347742]  sdb:<6>sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[36093.117570] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[36093.117579] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[36093.117585] end_request: I/O error, dev sdb, sector 0
[36093.117593] Buffer I/O error on device sdb, logical block 0
[36101.681825] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[36101.681835] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[36101.681841] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[36101.681848] end_request: I/O error, dev sdb, sector 0
[36101.681855] Buffer I/O error on device sdb, logical block 0
[36111.911953] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[36111.911963] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[36111.911969] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[36111.911976] end_request: I/O error, dev sdb, sector 0
[36111.911983] Buffer I/O error on device sdb, logical block 0
[36111.926081] ldm_validate_partition_table(): Disk read failed.
[36111.926092] Dev sdb: unable to read RDB block 0
[36111.937328]  unable to read partition table
[36111.940611] sd 2:0:0:0: [sdb] Attached SCSI disk
[36111.940718] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

Tried to mount:

```

root@home:~# mkdir /mnt/ext_hdd
root@home:~# mount -t ntfs /dev/sdb1 /mnt/ext_hdd/
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

```

The PC is clearly recognising the drive as being 2TB big - or 298.09GB (NTFS) with 1.71TB unallocated space according to Gparted. It is in fact merely 320GB (unless an incredibly lucky mistake was made when shipping it, but I doubt it). :D

Any thoughts? I've never done this before so am not sure if perhaps I'm just missing something. Maybe if I format it to FAT32 then back to NTFS in Gparted, or something?

---

### Post by SuaSwe on 2009-11-22
Ha! Never mind, you guys! I'd plugged it in using both USB outlets (not really knowing what I was doing, as mentioned :D) - tried with just one and there it is, all mounted and happy, and sadly not 2TB in capacity. ;)

---

