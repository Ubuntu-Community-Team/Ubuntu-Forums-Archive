---
title: "HELP!!! i think i busted my ipod..."
date: 2009-02-10
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-02-10
hi all,

i have been working nonstop for like 10 hours trying to "fix" my 5g 80gb video ipod. according to the ipod, it needs a restore (but when i restore w/windows, it just says the same thing again; i've done it 3 times now). my intrepid laptop doesnt even see it, however. i know, after using testdisk, that the drive should be /dev/sdb. however, here is my fdisk -l output:

```
j@j-laptop:/media$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1932    15518758+  83  Linux
/dev/sda2            1934        5630    29696152+  83  Linux
/dev/sda3   *        5631        9356    29929095    7  HPFS/NTFS
/dev/sda4            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris

```

as you can see, nothin there... i tried 'mounting by hand' with:

```
sudo mount -a

sudo mount -t vfat /dev/sdb /media/iPod


```

to which i get:

```
mount: /dev/sdb: can't read superblock
```

actually, this is the first time i've seen that ^^^:confused:

here is dmesg output, starting from the "important" part:
```

[   90.192079] usb 3-1: new high speed USB device using ehci_hcd and address 2
[   90.344091] usb 3-1: configuration #1 chosen from 2 choices
[   90.547675] usbcore: registered new interface driver libusual
[   90.590609] Initializing USB Mass Storage driver...
[   90.594765] scsi2 : SCSI emulation for USB Mass Storage devices
[   90.604125] usbcore: registered new interface driver usb-storage
[   90.604721] USB Mass Storage support registered.
[   90.605370] usb-storage: device found at 2
[   90.605377] usb-storage: waiting for device to settle before scanning
[   95.604361] usb-storage: device scan complete
[   95.613087] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   95.619326] sd 2:0:0:0: [sdb] 19521239 4096-byte hardware sectors (79959 MB)
[   95.624089] sd 2:0:0:0: [sdb] Write Protect is off
[   95.624101] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[   95.624107] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   95.627884] sd 2:0:0:0: [sdb] 19521239 4096-byte hardware sectors (79959 MB)
[   95.629280] sd 2:0:0:0: [sdb] Write Protect is off
[   95.629289] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[   95.629294] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   95.632920]  sdb:<6>sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  100.631256] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  100.631269] Info fld=0x0
[  100.631273] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  100.631283] end_request: I/O error, dev sdb, sector 0
[  100.631293] Buffer I/O error on device sdb, logical block 0
[  105.631842] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  105.631857] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  105.631867] Info fld=0x0
[  105.631871] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  105.631880] end_request: I/O error, dev sdb, sector 0
[  105.631891] Buffer I/O error on device sdb, logical block 0
[  110.630542] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  110.630558] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  110.630569] Info fld=0x0
[  110.630573] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  110.630584] end_request: I/O error, dev sdb, sector 0
[  110.630594] Buffer I/O error on device sdb, logical block 0
[  115.631123] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  115.631139] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  115.631148] Info fld=0x0
[  115.631152] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  115.631161] end_request: I/O error, dev sdb, sector 0
[  115.631172] Buffer I/O error on device sdb, logical block 0
[  120.634830] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  120.634846] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  120.634856] Info fld=0x0
[  120.634859] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  120.634869] end_request: I/O error, dev sdb, sector 0
[  120.634879] Buffer I/O error on device sdb, logical block 0
[  120.634906] ldm_validate_partition_table(): Disk read failed.
[  125.643537] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  125.643552] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  125.643562] Info fld=0x0
[  125.643566] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  125.643576] end_request: I/O error, dev sdb, sector 0
[  125.643586] Buffer I/O error on device sdb, logical block 0
[  130.646252] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  130.646268] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  130.646278] Info fld=0x0
[  130.646282] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  130.646292] end_request: I/O error, dev sdb, sector 0
[  130.646303] Buffer I/O error on device sdb, logical block 0
[  135.646836] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  135.646852] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  135.646862] Info fld=0x0
[  135.646866] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  135.646876] end_request: I/O error, dev sdb, sector 0
[  135.646886] Buffer I/O error on device sdb, logical block 0
[  140.647672] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  140.647688] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  140.647699] Info fld=0x0
[  140.647703] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  140.647713] end_request: I/O error, dev sdb, sector 0
[  140.647725] Buffer I/O error on device sdb, logical block 0
[  140.647762] Dev sdb: unable to read RDB block 0
[  145.648123] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  145.648156] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  145.648167] Info fld=0x0
[  145.648170] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  145.648180] end_request: I/O error, dev sdb, sector 0
[  145.648191] Buffer I/O error on device sdb, logical block 0
[  150.648825] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  150.648840] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  150.648850] Info fld=0x0
[  150.648854] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  150.648864] end_request: I/O error, dev sdb, sector 0
[  150.648875] Buffer I/O error on device sdb, logical block 0
[  155.649521] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  155.649530] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  155.649535] Info fld=0x0
[  155.649537] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  155.649542] end_request: I/O error, dev sdb, sector 24
[  155.649549] Buffer I/O error on device sdb, logical block 3
[  160.648244] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  160.648260] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  160.648270] Info fld=0x0
[  160.648274] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  160.648284] end_request: I/O error, dev sdb, sector 24
[  160.648295] Buffer I/O error on device sdb, logical block 3
[  165.648816] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  165.648832] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  165.648842] Info fld=0x0
[  165.648846] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  165.648856] end_request: I/O error, dev sdb, sector 0
[  165.648867] Buffer I/O error on device sdb, logical block 0
[  170.649540] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  170.649556] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  170.649566] Info fld=0x0
[  170.649569] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  170.649579] end_request: I/O error, dev sdb, sector 0
[  170.649590] Buffer I/O error on device sdb, logical block 0
[  170.649625]  unable to read partition table
[  170.659898] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  170.662215] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  175.723221] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  175.723237] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  175.723247] Info fld=0x0
[  175.723251] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  175.723261] end_request: I/O error, dev sdb, sector 0
[  175.723271] Buffer I/O error on device sdb, logical block 0
[  175.723282] Buffer I/O error on device sdb, logical block 1
[  175.723288] Buffer I/O error on device sdb, logical block 2
[  175.723294] Buffer I/O error on device sdb, logical block 3
[  180.724784] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  180.724800] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  180.724810] Info fld=0x0
[  180.724814] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  180.724824] end_request: I/O error, dev sdb, sector 0
[  180.724834] Buffer I/O error on device sdb, logical block 0
[  185.825491] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  185.825507] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  185.825517] Info fld=0x0
[  185.825521] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  185.825531] end_request: I/O error, dev sdb, sector 0
[  185.825542] Buffer I/O error on device sdb, logical block 0
[  185.825553] Buffer I/O error on device sdb, logical block 1
[  185.825560] Buffer I/O error on device sdb, logical block 2
[  185.825566] Buffer I/O error on device sdb, logical block 3
[  190.827060] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  190.827076] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  190.827086] Info fld=0x0
[  190.827090] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  190.827099] end_request: I/O error, dev sdb, sector 0
[  190.827110] Buffer I/O error on device sdb, logical block 0
[  198.477629] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  198.477645] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  198.477655] Info fld=0x0
[  198.477658] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  198.477668] end_request: I/O error, dev sdb, sector 0
[  198.477679] Buffer I/O error on device sdb, logical block 0
[  198.477691] Buffer I/O error on device sdb, logical block 1
[  198.477697] Buffer I/O error on device sdb, logical block 2
[  198.477703] Buffer I/O error on device sdb, logical block 3
[  203.487041] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  203.487057] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  203.487067] Info fld=0x0
[  203.487071] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  203.487081] end_request: I/O error, dev sdb, sector 0
[  203.487090] Buffer I/O error on device sdb, logical block 0
[  593.843362] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  593.843378] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  593.843389] Info fld=0x0
[  593.843392] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  593.843402] end_request: I/O error, dev sdb, sector 8
[  593.843413] Buffer I/O error on device sdb, logical block 1
[  598.846447] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  598.846463] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  598.846473] Info fld=0x0
[  598.846477] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  598.846487] end_request: I/O error, dev sdb, sector 8
[  598.846498] Buffer I/O error on device sdb, logical block 1
[  603.887785] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  603.887801] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  603.887811] Info fld=0x0
[  603.887815] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  603.887825] end_request: I/O error, dev sdb, sector 0
[  603.887835] Buffer I/O error on device sdb, logical block 0
[  608.890872] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  608.890888] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  608.890898] Info fld=0x0
[  608.890901] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  608.890912] end_request: I/O error, dev sdb, sector 8
[  608.890922] Buffer I/O error on device sdb, logical block 1
[  608.890931] Buffer I/O error on device sdb, logical block 2
[  608.890937] Buffer I/O error on device sdb, logical block 3
[  613.894954] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  613.894970] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  613.894980] Info fld=0x0
[  613.894983] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  613.894993] end_request: I/O error, dev sdb, sector 0
[  613.895004] Buffer I/O error on device sdb, logical block 0
[  712.698762] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  712.698778] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  712.698788] Info fld=0x0
[  712.698792] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  712.698802] end_request: I/O error, dev sdb, sector 0
[  712.698841] FAT: unable to read boot sector
[  794.734172] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  794.734188] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  794.734198] Info fld=0x0
[  794.734201] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  794.734211] end_request: I/O error, dev sdb, sector 0
[  794.734221] Buffer I/O error on device sdb, logical block 0
[  799.737257] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  799.737273] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  799.737283] Info fld=0x0
[  799.737286] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  799.737295] end_request: I/O error, dev sdb, sector 0
[  799.737306] Buffer I/O error on device sdb, logical block 0
[  808.650600] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  808.650616] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  808.650626] Info fld=0x0
[  808.650630] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  808.650639] end_request: I/O error, dev sdb, sector 120
[  808.650650] Buffer I/O error on device sdb, logical block 15
[  813.653816] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  813.653832] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  813.653842] Info fld=0x0
[  813.653846] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  813.653855] end_request: I/O error, dev sdb, sector 128
[  813.653866] Buffer I/O error on device sdb, logical block 16
[  813.653875] Buffer I/O error on device sdb, logical block 17
[  818.657885] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  818.657901] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  818.657911] Info fld=0x0
[  818.657914] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  818.657924] end_request: I/O error, dev sdb, sector 120
[  818.657934] Buffer I/O error on device sdb, logical block 15
[  823.666987] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  823.667003] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  823.667013] Info fld=0x0
[  823.667016] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  823.667026] end_request: I/O error, dev sdb, sector 120
[  823.667037] Buffer I/O error on device sdb, logical block 15
[  828.673062] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  828.673077] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  828.673087] Info fld=0x0
[  828.673090] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  828.673100] end_request: I/O error, dev sdb, sector 128
[  828.673110] Buffer I/O error on device sdb, logical block 16
[  833.682396] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  833.682413] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  833.682423] Info fld=0x0
[  833.682426] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  833.682436] end_request: I/O error, dev sdb, sector 56
[  833.682447] Buffer I/O error on device sdb, logical block 7
[  833.682459] Buffer I/O error on device sdb, logical block 8
[  838.686371] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  838.686387] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  838.686398] Info fld=0x0
[  838.686401] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  838.686411] end_request: I/O error, dev sdb, sector 56
[  838.686422] Buffer I/O error on device sdb, logical block 7
[  843.689570] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  843.689586] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  843.689596] Info fld=0x0
[  843.689600] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  843.689610] end_request: I/O error, dev sdb, sector 8
[  843.689620] Buffer I/O error on device sdb, logical block 1
[  848.693680] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  848.693695] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  848.693705] Info fld=0x0
[  848.693709] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  848.693719] end_request: I/O error, dev sdb, sector 0
[  848.693730] Buffer I/O error on device sdb, logical block 0
[  853.702866] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  853.702882] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  853.702892] Info fld=0x0
[  853.702895] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  853.702905] end_request: I/O error, dev sdb, sector 0
[  853.702916] Buffer I/O error on device sdb, logical block 0
[  906.149407] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  906.149423] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  906.149433] Info fld=0x0
[  906.149437] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  906.149447] end_request: I/O error, dev sdb, sector 48
[  906.149458] Buffer I/O error on device sdb, logical block 6
[  911.153472] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  911.153481] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  911.153486] Info fld=0x0
[  911.153488] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  911.153493] end_request: I/O error, dev sdb, sector 48
[  911.153500] Buffer I/O error on device sdb, logical block 6
```

now, i don't know what any of that means, but i see to many instances of "error" to think its a good thing.

can anybody point me in the right direction here? all help is, of course, appreciated.

jmd9qs

---

### Post by blueridgedog on 2009-02-10
Have you tried resetting your ipod?  Press the middle button and the menu button for 6-12 seconds until the apple logo appears.

---

### Post by LowSky on 2009-02-10
flip hold on then off then press the center button and menu for about 6 seconds, it should reset the ipod

if that don't work, reformate it using Gparted (might break it so be careful before you do it)

---

### Post by jmd9qs on 2009-02-10
thanks for the replies, guys!

unfortunately, i've tried both of those things many times. resetting the ipod just brings me back to the "use iTunes to restore" screen.

when i try to use gparted to reformat, here is what i get:
```

j@j-laptop:~$ sudo gparted
[sudo] password for j: 
Sorry, try again.
[sudo] password for j: 
======================
libparted : 1.8.9
======================
Device /dev/sdb has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Input/output error during read on /dev/sdb


```

when gparted's gui finally loads, sdb is nowhere to be found.

---

