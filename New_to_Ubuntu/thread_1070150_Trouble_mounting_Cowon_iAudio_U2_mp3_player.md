---
title: "Trouble mounting Cowon iAudio U2 mp3 player"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by mschersten on 2009-02-14
I'm not quite a newbie, but it will probably be best if you treat me like one.

I picked up a Cowon iAudio U2 the other day.  I have tried it with a Windows machine, and the player itself seems to be working fine, but I just can't get it to mount in Ubuntu.  Here's what I get from lsusb:

```
michael@michael-desktop:~$ lsusb
Bus 002 Device 002: ID 0e21:0600 Cowon Systems, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Here's what I get from dmesg after plugging it in:

```
[  954.720105] usb 2-1: USB disconnect, address 2
[  991.124051] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  991.339995] usb 2-1: configuration #1 chosen from 1 choice
[  991.373020] scsi3 : SCSI emulation for USB Mass Storage devices
[  991.374677] usb-storage: device found at 3
[  991.374689] usb-storage: waiting for device to settle before scanning
[  996.373326] usb-storage: device scan complete
[  996.377287] scsi 3:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[  996.397900] sd 3:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[  996.401222] sd 3:0:0:0: [sdb] Write Protect is off
[  996.401239] sd 3:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[  996.401246] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  996.414479] sd 3:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[  996.468359] sd 3:0:0:0: [sdb] Write Protect is off
[  996.468377] sd 3:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[  996.468384] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  996.469775]  sdb: sdb1
[  996.479753] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  996.481016] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  996.892073] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  997.220074] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  997.492035] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  997.772035] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  998.040073] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  998.312075] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  998.461930] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  998.461953] end_request: I/O error, dev sdb, sector 4100480
[  998.461968] Buffer I/O error on device sdb, logical block 512560
[  998.580040] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  998.848071] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  999.124074] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  999.384035] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  999.656057] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  999.920074] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1000.069645] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1000.069670] end_request: I/O error, dev sdb, sector 4100480
[ 1000.069685] Buffer I/O error on device sdb, logical block 512560
[ 1000.188050] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1000.456035] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1000.720064] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1000.996099] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1001.260086] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1001.536109] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1001.685381] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1001.685405] end_request: I/O error, dev sdb, sector 4100592
[ 1001.685420] Buffer I/O error on device sdb, logical block 512574
[ 1001.804070] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1002.080037] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1002.344056] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1002.612085] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1002.880033] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1003.148035] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1003.301120] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1003.301144] end_request: I/O error, dev sdb, sector 4100592
[ 1003.301159] Buffer I/O error on device sdb, logical block 512574
[ 1003.420036] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1003.688075] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1003.960068] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1004.228058] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1004.504051] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1004.776051] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1004.925855] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1004.925880] end_request: I/O error, dev sdb, sector 32
[ 1004.925894] Buffer I/O error on device sdb, logical block 4
[ 1005.044074] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1005.308037] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1005.576032] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1005.852035] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1006.116059] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1006.384070] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1006.532591] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1006.532615] end_request: I/O error, dev sdb, sector 40
[ 1006.532629] Buffer I/O error on device sdb, logical block 5
[ 1006.652061] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1006.924343] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1007.188074] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1007.464056] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1007.732073] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1008.004074] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[ 1011.961724] usb 2-1: device firmware changed
[ 1011.963062] usb 2-1: USB disconnect, address 3
[ 1011.970435] scsi 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1011.970454] end_request: I/O error, dev sdb, sector 4100600
[ 1011.970468] Buffer I/O error on device sdb, logical block 512575
[ 1011.970555] Buffer I/O error on device sdb, logical block 512575
[ 1011.970641] Buffer I/O error on device sdb, logical block 512575
[ 1011.970677] Buffer I/O error on device sdb, logical block 512575
[ 1011.970711] Buffer I/O error on device sdb, logical block 512575
[ 1011.970746] Buffer I/O error on device sdb, logical block 512575
[ 1011.970781] Buffer I/O error on device sdb, logical block 512575
[ 1011.970844] Buffer I/O error on device sdb, logical block 512568
[ 1011.970887] Buffer I/O error on device sdb, logical block 512574
[ 1011.971726] scsi 3:0:0:0: rejecting I/O to dead device
[ 1012.096112] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 1012.283071] usb 2-1: configuration #1 chosen from 1 choice
[ 1012.305870] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1012.306813] usb-storage: device found at 4
[ 1012.306824] usb-storage: waiting for device to settle before scanning
[ 1017.305931] usb-storage: device scan complete
[ 1017.309915] scsi 4:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[ 1017.331821] sd 4:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[ 1017.335873] sd 4:0:0:0: [sdb] Write Protect is off
[ 1017.335889] sd 4:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[ 1017.335896] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1017.397108] sd 4:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[ 1017.401599] sd 4:0:0:0: [sdb] Write Protect is off
[ 1017.401619] sd 4:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[ 1017.401626] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1017.402914]  sdb:<6>usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1017.788060] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1018.052035] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1018.324051] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1018.588075] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1018.856043] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1019.009554] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1019.009576] end_request: I/O error, dev sdb, sector 0
[ 1019.009587] __ratelimit: 12 callbacks suppressed
[ 1019.009595] Buffer I/O error on device sdb, logical block 0
[ 1019.128061] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1019.400057] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1019.664063] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1019.932036] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1020.200056] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1020.472093] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1020.621311] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1020.621335] end_request: I/O error, dev sdb, sector 0
[ 1020.621350] Buffer I/O error on device sdb, logical block 0
[ 1020.740035] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1021.020071] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1021.284120] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1021.556070] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1021.824087] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1022.096035] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1022.250055] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1022.250079] end_request: I/O error, dev sdb, sector 0
[ 1022.250094] Buffer I/O error on device sdb, logical block 0
[ 1022.364057] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1022.632038] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1022.896062] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1023.168080] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1023.434137] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1023.704069] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1023.861800] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1023.861825] end_request: I/O error, dev sdb, sector 0
[ 1023.861841] Buffer I/O error on device sdb, logical block 0
[ 1023.980069] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1024.244062] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1024.516039] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1024.784037] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1025.048062] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1025.320062] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1025.477584] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1025.477610] end_request: I/O error, dev sdb, sector 0
[ 1025.477627] Buffer I/O error on device sdb, logical block 0
[ 1025.477679] ldm_validate_partition_table(): Disk read failed.
[ 1025.596173] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1025.868100] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1026.136181] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1026.401822] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1026.668035] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1026.936054] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1027.087260] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1027.087283] end_request: I/O error, dev sdb, sector 0
[ 1027.087297] Buffer I/O error on device sdb, logical block 0
[ 1027.204036] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1027.472036] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1027.744069] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1028.068038] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1028.344073] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1028.616067] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1028.766032] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1028.766056] end_request: I/O error, dev sdb, sector 0
[ 1028.766070] Buffer I/O error on device sdb, logical block 0
[ 1028.884052] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1029.152062] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1029.416075] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1029.680035] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1029.956090] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1030.224052] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1030.379738] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1030.379762] end_request: I/O error, dev sdb, sector 0
[ 1030.379777] Buffer I/O error on device sdb, logical block 0
[ 1030.504051] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1030.768058] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1031.032073] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1031.320102] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1031.588036] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1031.856053] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1032.014615] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1032.014646] end_request: I/O error, dev sdb, sector 0
[ 1032.014664] Buffer I/O error on device sdb, logical block 0
[ 1032.014731] Dev sdb: unable to read RDB block 0
[ 1032.132118] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1032.404034] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[ 1032.555326] usb 2-1: failed to restore interface 0 altsetting 0 (error=-84)
[ 1032.557149] usb 2-1: USB disconnect, address 4
[ 1032.564081] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1032.564101] end_request: I/O error, dev sdb, sector 0
[ 1032.564116] Buffer I/O error on device sdb, logical block 0
[ 1032.568066] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1032.568095] end_request: I/O error, dev sdb, sector 0
[ 1032.568109] Buffer I/O error on device sdb, logical block 0
[ 1032.569667] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1032.569689] end_request: I/O error, dev sdb, sector 24
[ 1032.569700] Buffer I/O error on device sdb, logical block 3
[ 1032.572038] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1032.572052] end_request: I/O error, dev sdb, sector 24
[ 1032.572063] Buffer I/O error on device sdb, logical block 3
[ 1032.576026] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1032.576040] end_request: I/O error, dev sdb, sector 0
[ 1032.576049] Buffer I/O error on device sdb, logical block 0
[ 1032.577379] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1032.577396] end_request: I/O error, dev sdb, sector 0
[ 1032.577406] Buffer I/O error on device sdb, logical block 0
[ 1032.577500]  unable to read partition table
[ 1032.578754] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1032.579316] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1032.692114] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 1032.876484] usb 2-1: configuration #1 chosen from 1 choice
[ 1032.932123] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1032.933766] usb-storage: device found at 5
[ 1032.933778] usb-storage: waiting for device to settle before scanning
[ 1037.933573] usb-storage: device scan complete
[ 1037.940558] scsi 5:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[ 1037.960477] sd 5:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[ 1037.963518] sd 5:0:0:0: [sdb] Write Protect is off
[ 1037.963537] sd 5:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[ 1037.963544] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1037.974307] sd 5:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[ 1038.028074] sd 5:0:0:0: [sdb] Write Protect is off
[ 1038.028092] sd 5:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[ 1038.028099] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1038.029348]  sdb:<6>usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1038.416036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1038.696118] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1038.965900] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1039.240071] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1039.508051] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1039.657224] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1039.657248] end_request: I/O error, dev sdb, sector 0
[ 1039.657263] Buffer I/O error on device sdb, logical block 0
[ 1039.776074] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1040.044296] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1040.312036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1040.584051] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1040.860074] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1041.132075] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1041.281957] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1041.281982] end_request: I/O error, dev sdb, sector 0
[ 1041.281996] Buffer I/O error on device sdb, logical block 0
[ 1041.400056] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1041.664616] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1041.940054] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1042.212036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1042.476051] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1042.744071] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1042.893694] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1042.893718] end_request: I/O error, dev sdb, sector 0
[ 1042.893733] Buffer I/O error on device sdb, logical block 0
[ 1043.012046] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1043.280055] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1043.548052] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1043.816072] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1044.080049] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1044.344234] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1044.492428] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1044.492452] end_request: I/O error, dev sdb, sector 0
[ 1044.492469] Buffer I/O error on device sdb, logical block 0
[ 1044.608073] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1044.876064] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1045.144037] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1045.420056] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1045.688068] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1045.956099] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1046.122215] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1046.122241] end_request: I/O error, dev sdb, sector 0
[ 1046.122257] Buffer I/O error on device sdb, logical block 0
[ 1046.122306] ldm_validate_partition_table(): Disk read failed.
[ 1046.244101] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1046.525250] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1046.796115] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1047.072052] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1047.340070] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1047.605495] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1047.757898] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1047.757922] end_request: I/O error, dev sdb, sector 0
[ 1047.757936] Buffer I/O error on device sdb, logical block 0
[ 1047.880120] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1048.144099] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1048.416898] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1048.684060] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1048.956056] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1049.220054] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1049.370774] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1049.370799] end_request: I/O error, dev sdb, sector 0
[ 1049.370814] Buffer I/O error on device sdb, logical block 0
[ 1049.492033] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1049.760036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1050.028052] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1050.292071] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1050.560041] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1050.828075] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1050.976384] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1050.976407] end_request: I/O error, dev sdb, sector 0
[ 1050.976422] Buffer I/O error on device sdb, logical block 0
[ 1051.092129] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1051.360034] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1051.632093] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1051.900073] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1052.164034] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1052.488041] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1052.698102] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1052.698126] end_request: I/O error, dev sdb, sector 0
[ 1052.698140] Buffer I/O error on device sdb, logical block 0
[ 1052.698185] Dev sdb: unable to read RDB block 0
[ 1052.812052] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1053.088067] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1053.360036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1053.628067] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1053.896086] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1054.168101] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1054.317838] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1054.317862] end_request: I/O error, dev sdb, sector 0
[ 1054.317877] Buffer I/O error on device sdb, logical block 0
[ 1054.440051] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1054.708211] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1054.980072] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1055.248038] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1055.513972] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1055.659570] usb 2-1: device descriptor read/all, error -71
[ 1055.772163] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1056.044073] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1056.195534] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1056.195558] end_request: I/O error, dev sdb, sector 0
[ 1056.195573] Buffer I/O error on device sdb, logical block 0
[ 1056.312072] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1056.580045] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1056.848038] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1057.112124] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1057.384096] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1057.656121] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1057.808277] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1057.808300] end_request: I/O error, dev sdb, sector 24
[ 1057.808315] Buffer I/O error on device sdb, logical block 3
[ 1057.932051] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1058.196064] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1058.464043] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1058.740052] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1059.012051] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1059.284060] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1059.434008] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1059.434032] end_request: I/O error, dev sdb, sector 24
[ 1059.434047] Buffer I/O error on device sdb, logical block 3
[ 1059.552065] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1059.820086] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1060.084033] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1060.360034] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1060.624045] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1060.900058] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1061.050837] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1061.050861] end_request: I/O error, dev sdb, sector 0
[ 1061.050876] Buffer I/O error on device sdb, logical block 0
[ 1061.172049] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1061.436092] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1061.712066] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1061.976036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1062.244054] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1062.512066] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1062.661484] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1062.661508] end_request: I/O error, dev sdb, sector 0
[ 1062.661523] Buffer I/O error on device sdb, logical block 0
[ 1062.661567]  unable to read partition table
[ 1062.673946] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 1062.674942] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 1062.948088] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1063.212053] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1063.480037] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1063.752071] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1064.020052] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1064.292036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1064.443198] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1064.443222] end_request: I/O error, dev sdb, sector 0
[ 1064.443237] Buffer I/O error on device sdb, logical block 0
[ 1064.443252] Buffer I/O error on device sdb, logical block 1
[ 1064.443261] Buffer I/O error on device sdb, logical block 2
[ 1064.443269] Buffer I/O error on device sdb, logical block 3
[ 1064.560112] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1064.888070] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1065.160072] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1065.428058] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1065.692036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1065.972084] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1066.125924] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1066.125948] end_request: I/O error, dev sdb, sector 0
[ 1066.125963] Buffer I/O error on device sdb, logical block 0
[ 1066.288072] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1066.560072] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1066.836075] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1067.104036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1067.372070] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1067.636081] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1067.785655] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1067.785679] end_request: I/O error, dev sdb, sector 0
[ 1067.785693] Buffer I/O error on device sdb, logical block 0
[ 1067.785710] Buffer I/O error on device sdb, logical block 1
[ 1067.785718] Buffer I/O error on device sdb, logical block 2
[ 1067.785726] Buffer I/O error on device sdb, logical block 3
[ 1067.912036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1068.176209] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1068.440036] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1068.704083] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1068.968078] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1069.236042] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1069.385394] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1069.385418] end_request: I/O error, dev sdb, sector 0
[ 1069.385432] Buffer I/O error on device sdb, logical block 0
[ 1071.596052] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1071.872118] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1072.140070] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1072.408038] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1072.672035] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1072.940048] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1073.089798] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1073.089821] end_request: I/O error, dev sdb, sector 0
[ 1073.089835] Buffer I/O error on device sdb, logical block 0
[ 1073.089851] Buffer I/O error on device sdb, logical block 1
[ 1073.089859] Buffer I/O error on device sdb, logical block 2
[ 1073.089867] Buffer I/O error on device sdb, logical block 3
[ 1073.214100] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1073.488086] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1073.756032] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1074.020054] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1074.284058] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1074.552056] usb 2-1: reset full speed USB device using uhci_hcd and address 5
[ 1074.701531] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1074.701555] end_request: I/O error, dev sdb, sector 0
[ 1074.701570] Buffer I/O error on device sdb, logical block 0
[ 1133.580037] usb 2-1: reset full speed USB device using uhci_hcd and address 5

```

I created a directory in /media:
```
michael@michael-desktop:~$ ls -la /media
total 16
drwxr-xr-x  4 root root 4096 2009-02-14 18:50 .
drwxr-xr-x 20 root root 4096 2009-01-28 19:44 ..
lrwxrwxrwx  1 root root    6 2008-11-04 12:37 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-11-04 12:37 cdrom0
-rw-r--r--  1 root root    0 2009-02-14 18:50 .hal-mtab
drwxr-xr-x  2 root root 4096 2009-02-14 13:14 mp3

```

From dmesg, I guessed that it was sdb, so then I try to mount:
```
michael@michael-desktop:~$ sudo mount /dev/sdb /media/mp3
mount: you must specify the filesystem type

```

I don't know the filesystem type, and I'm not sure how to find out, but if I try vfat:
```
michael@michael-desktop:~$ sudo mount -t vfat /dev/sdb /media/mp3
mount: /dev/sdb: can't read superblock

```

Any advice?

---

### Post by bsharp on 2009-02-14
You were close, /dev/sdb is the device. /dev/sdb**1** is probably the partition.

```
sudo mount -t vfat /dev/sdb1 /media/mp3
```

That should do it.

---

### Post by mschersten on 2009-02-14
Thanks.  That didn't work, but at least it gave me a new message :)

```
michael@michael-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/mp3
mount: special device /dev/sdb1 does not exist

```

---

### Post by mschersten on 2009-02-14
```
michael@michael-desktop:/media$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-02-14 18:49 4ad719ba-d05f-4d5a-9b70-9c77bef3024f -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-02-14 18:49 9e4e1bee-7eaa-4d18-83f8-cc7c45e0565d -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-02-14 18:49 af33e889-2ac8-431c-8d18-0c8ae708e15d -> ../../sda7

```

sda5 is swap, 6 & 7 are hard drive partitions.

---

### Post by mschersten on 2009-02-14
Here's something else:

```
michael@michael-desktop:/media$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39f539f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        2491    20008926    5  Extended
/dev/sda5            2387        2491      843412+  82  Linux swap / Solaris
/dev/sda6             602        2386    14337981   83  Linux
/dev/sda7               1         600     4819405+  83  Linux

Partition table entries are not in disk order

```

Still no sign of it.  I'm just trying stuff,  don't know what most of it means.  Any help would be great.

---

### Post by mschersten on 2009-02-15
So now I'm getting signs of sdc.  Here's dmesg since the last time plugging it in:

```
[22788.144104] usb 2-2: USB disconnect, address 65
[22790.368069] usb 2-2: new full speed USB device using uhci_hcd and address 66
[22790.544774] usb 2-2: configuration #1 chosen from 1 choice
[22790.602531] scsi184 : SCSI emulation for USB Mass Storage devices
[22790.610685] usb-storage: device found at 66
[22790.610709] usb-storage: waiting for device to settle before scanning
[22795.610168] usb-storage: device scan complete
[22795.614192] scsi 184:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[22795.634094] sd 184:0:0:0: [sdc] 1025152 2048-byte hardware sectors (2100 MB)
[22795.637069] sd 184:0:0:0: [sdc] Write Protect is off
[22795.637087] sd 184:0:0:0: [sdc] Mode Sense: 3e 00 00 00
[22795.637093] sd 184:0:0:0: [sdc] Assuming drive cache: write through
[22795.648563] sd 184:0:0:0: [sdc] 1025152 2048-byte hardware sectors (2100 MB)
[22795.700203] sd 184:0:0:0: [sdc] Write Protect is off
[22795.700222] sd 184:0:0:0: [sdc] Mode Sense: 3e 00 00 00
[22795.700230] sd 184:0:0:0: [sdc] Assuming drive cache: write through
[22795.701490]  sdc: sdc1
[22795.715113] sd 184:0:0:0: [sdc] Attached SCSI removable disk
[22795.716229] sd 184:0:0:0: Attached scsi generic sg3 type 0
[22796.212048] usb 2-2: reset full speed USB device using uhci_hcd and address 66
[22796.476048] usb 2-2: reset full speed USB device using uhci_hcd and address 66
[22796.748060] usb 2-2: reset full speed USB device using uhci_hcd and address 66
[22797.012062] usb 2-2: reset full speed USB device using uhci_hcd and address 66
[22797.280098] usb 2-2: reset full speed USB device using uhci_hcd and address 66
[22797.548076] usb 2-2: reset full speed USB device using uhci_hcd and address 66
[22797.697750] sd 184:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22797.697775] end_request: I/O error, dev sdc, sector 0
[22797.697789] Buffer I/O error on device sdc, logical block 0
[22797.697805] Buffer I/O error on device sdc, logical block 1
[22797.697813] Buffer I/O error on device sdc, logical block 2
[22797.697821] Buffer I/O error on device sdc, logical block 3

[22815.853810] sd 184:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22815.853834] end_request: I/O error, dev sdc, sector 0
[22815.853848] Buffer I/O error on device sdc, logical block 0
[22816.004051] usb 2-2: reset full speed USB device using uhci_hcd and address 66
[22816.530681] usb 2-2: can't restore configuration #1 (error=-84)
[22816.532444] usb 2-2: USB disconnect, address 66
[22816.540154] scsi 184:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[22816.540173] end_request: I/O error, dev sdc, sector 0
[22816.540186] Buffer I/O error on device sdc, logical block 0
[22816.540360] Buffer I/O error on device sdc, logical block 0
[22816.541722] scsi 184:0:0:0: rejecting I/O to dead device
[22816.656124] usb 2-2: new full speed USB device using uhci_hcd and address 67
[22816.895693] usb 2-2: configuration #1 chosen from 1 choice
[22816.957882] scsi185 : SCSI emulation for USB Mass Storage devices
[22816.958859] usb-storage: device found at 67
[22816.958871] usb-storage: waiting for device to settle before scanning
[22821.957891] usb-storage: device scan complete
[22821.961844] scsi 185:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[22821.979791] sd 185:0:0:0: [sdc] 1025152 2048-byte hardware sectors (2100 MB)
[22821.983803] sd 185:0:0:0: [sdc] Write Protect is off
[22821.983822] sd 185:0:0:0: [sdc] Mode Sense: 3e 00 00 00
[22821.983829] sd 185:0:0:0: [sdc] Assuming drive cache: write through
[22822.040070] sd 185:0:0:0: [sdc] 1025152 2048-byte hardware sectors (2100 MB)
[22822.048166] sd 185:0:0:0: [sdc] Write Protect is off
[22822.048185] sd 185:0:0:0: [sdc] Mode Sense: 3e 00 00 00
[22822.048192] sd 185:0:0:0: [sdc] Assuming drive cache: write through
[22822.049451]  sdc:<6>usb 2-2: reset full speed USB device using uhci_hcd and address 67
[22822.436053] usb 2-2: reset full speed USB device using uhci_hcd and address 67
[22822.704061] usb 2-2: reset full speed USB device using uhci_hcd and address 67
[22822.976053] usb 2-2: reset full speed USB device using uhci_hcd and address 67
[22823.244050] usb 2-2: reset full speed USB device using uhci_hcd and address 67
[22823.512067] usb 2-2: reset full speed USB device using uhci_hcd and address 67
[22823.663590] sd 185:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22823.663616] end_request: I/O error, dev sdc, sector 0
[22823.663631] Buffer I/O error on device sdc, logical block 0

[22843.949202] usb 2-2: failed to restore interface 0 altsetting 0 (error=-84)
[22843.951082] sd 185:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22843.951100] end_request: I/O error, dev sdc, sector 0
[22843.951113] Buffer I/O error on device sdc, logical block 0
[22843.952523] usb 2-2: USB disconnect, address 67
[22843.960045] sd 185:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[22843.960065] end_request: I/O error, dev sdc, sector 0
[22843.960080] Buffer I/O error on device sdc, logical block 0
[22843.960120]  unable to read partition table
[22843.964734] sd 185:0:0:0: [sdc] Attached SCSI removable disk
[22843.965078] sd 185:0:0:0: Attached scsi generic sg3 type 0
[22844.076067] usb 2-2: new full speed USB device using uhci_hcd and address 68
[22844.236544] usb 2-2: configuration #1 chosen from 1 choice
[22844.301055] scsi186 : SCSI emulation for USB Mass Storage devices
[22844.302647] usb-storage: device found at 68
[22844.302659] usb-storage: waiting for device to settle before scanning
[22849.301457] usb-storage: device scan complete
[22849.306513] scsi 186:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[22849.334990] sd 186:0:0:0: [sdc] 1025152 2048-byte hardware sectors (2100 MB)
[22849.364239] sd 186:0:0:0: [sdc] Write Protect is off
[22849.364257] sd 186:0:0:0: [sdc] Mode Sense: 3e 00 00 00
[22849.364264] sd 186:0:0:0: [sdc] Assuming drive cache: write through
[22849.385710] sd 186:0:0:0: [sdc] 1025152 2048-byte hardware sectors (2100 MB)
[22849.390438] sd 186:0:0:0: [sdc] Write Protect is off
[22849.390457] sd 186:0:0:0: [sdc] Mode Sense: 3e 00 00 00
[22849.390464] sd 186:0:0:0: [sdc] Assuming drive cache: write through
[22849.391751]  sdc:<6>usb 2-2: reset full speed USB device using uhci_hcd and address 68
[22849.792073] usb 2-2: reset full speed USB device using uhci_hcd and address 68
[22850.056059] usb 2-2: reset full speed USB device using uhci_hcd and address 68
[22850.320069] usb 2-2: reset full speed USB device using uhci_hcd and address 68
[22850.584075] usb 2-2: reset full speed USB device using uhci_hcd and address 68
[22850.912068] usb 2-2: reset full speed USB device using uhci_hcd and address 68
[22851.066085] sd 186:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22851.066108] end_request: I/O error, dev sdc, sector 0
[22851.066123] Buffer I/O error on device sdc, logical block 0
[22851.188066] usb 2-2: reset full speed USB device using uhci_hcd and address 68
[22851.468059] usb 2-2: reset full speed USB device using uhci_hcd and address 68
[22852.765794] usb 2-2: can't restore configuration #1 (error=-84)
[22852.767361] usb 2-2: USB disconnect, address 68
[22852.774145] sd 186:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK

[22852.787579] sd 186:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[22852.787589] end_request: I/O error, dev sdc, sector 0
[22852.787608]  unable to read partition table
[22852.787885] sd 186:0:0:0: [sdc] Attached SCSI removable disk
[22852.788281] sd 186:0:0:0: Attached scsi generic sg3 type 0
[22852.900874] usb 2-2: new full speed USB device using uhci_hcd and address 69
[22853.065649] usb 2-2: configuration #1 chosen from 1 choice
[22853.084868] scsi187 : SCSI emulation for USB Mass Storage devices
[22853.085784] usb-storage: device found at 69
[22853.085795] usb-storage: waiting for device to settle before scanning
[22858.086029] usb-storage: device scan complete
[22858.089990] scsi 187:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[22858.114070] sd 187:0:0:0: [sdc] 1025152 2048-byte hardware sectors (2100 MB)
[22858.169852] sd 187:0:0:0: [sdc] Write Protect is off
[22858.169869] sd 187:0:0:0: [sdc] Mode Sense: 3e 00 00 00
[22858.169876] sd 187:0:0:0: [sdc] Assuming drive cache: write through
[22858.189261] sd 187:0:0:0: [sdc] 1025152 2048-byte hardware sectors (2100 MB)
[22858.193220] sd 187:0:0:0: [sdc] Write Protect is off
[22858.193240] sd 187:0:0:0: [sdc] Mode Sense: 3e 00 00 00
[22858.193247] sd 187:0:0:0: [sdc] Assuming drive cache: write through
[22858.197164]  sdc:<6>usb 2-2: reset full speed USB device using uhci_hcd and address 69
[22858.592054] usb 2-2: reset full speed USB device using uhci_hcd and address 69
[22858.860073] usb 2-2: reset full speed USB device using uhci_hcd and address 69
[22859.132060] usb 2-2: reset full speed USB device using uhci_hcd and address 69
[22859.404053] usb 2-2: reset full speed USB device using uhci_hcd and address 69
[22859.672075] usb 2-2: reset full speed USB device using uhci_hcd and address 69
[22859.820667] sd 187:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22859.820691] end_request: I/O error, dev sdc, sector 0
[22859.820703] __ratelimit: 5 callbacks suppressed
[22859.820711] Buffer I/O error on device sdc, logical block 0

[23349.777143] sd 189:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[23349.777167] end_request: I/O error, dev sdc, sector 0
[23349.777181] Buffer I/O error on device sdc, logical block 0
[23538.984069] usb 2-2: reset full speed USB device using uhci_hcd and address 71

```

If I do this:
```
michael@michael-desktop:~$ sudo fdisk /dev/sdc

Unable to read /dev/sdc

```
It pauses a minute before printing that error message.

I can do this:
```
michael@michael-desktop:~$ sudo mount -fvrw -t vfat /dev/sdc /media/mp3
/dev/sdc on /media/mp3 type vfat (rw)

```

If I run mount:
```
michael@michael-desktop:~$ mount -l
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,relatime) []
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sdc on /media/mp3 type vfat (rw)

```

But /media/mp3 is empty.  Any ideas?

---

### Post by mschersten on 2009-02-15
Can anyone tell me if I should be able to mount, and am just using the wrong command or trying the wrong mount point, or if something in dmesg is telling me why I can't mount?

---

