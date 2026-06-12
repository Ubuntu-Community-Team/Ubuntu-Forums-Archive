---
title: "Webcam not detected"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by vvfrn on 2010-01-02
I used cheese and all I see is a black screen where the camera is supposed to be. Ubuntu also does not tell me when I connect my webcam This webcam works perfectly in Windows.What driver or steps should I install or do? THis is also a generic webcam and dos not have a brand name .
It's a USB webcam.
lusb terminal:
Bus 002 Device 044: ID 090c:b371 Feiya Technology Corp. Silicon Motion SM371 Camera
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Zzl1xndd on 2010-01-02
Plug in the camera, Open a terminal and type in dmesg. Then post the out put of the last line. Might give us some insight into what kind of camera and what is happening when you plug it in.

---

### Post by Methuselah on 2010-01-02
I am assuming it is a USB webcam.
Post the output of
```

lsusb

```
when run in a terminal.

That should give an idea of what kind of webcam you have.

---

### Post by charlier653 on 2010-01-02
Open synaptics, make sure you have  "all" highlighted in the left pane, and search for "webcam" and/or "camera".

I also have a generic webcam, that I got working by using fswebcam. Seems to play nice with cheese.

---

### Post by vvfrn on 2010-01-02
[SIZE="5"]**lusb terminal:**[/SIZE]
Bus 002 Device 044: ID 090c:b371 Feiya Technology Corp. Silicon Motion SM371 Camera
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[SIZE="5"]**dmesg terminal:**[/SIZE]
[ 6010.032143] usb 2-1: new full speed USB device using uhci_hcd and address 26
[ 6010.632144] usb 2-1: device not accepting address 26, error -71
[ 6010.688399] hub 2-0:1.0: unable to enumerate USB device on port 1
[ 6013.028155] usb 2-1: new full speed USB device using uhci_hcd and address 28
[ 6013.198750] usb 2-1: configuration #1 chosen from 1 choice
[ 6013.250928] scsi20 : SCSI emulation for USB Mass Storage devices
[ 6013.251311] usb-storage: device found at 28
[ 6013.251316] usb-storage: waiting for device to settle before scanning
[ 6015.408723] usb 2-1: USB disconnect, address 28
[ 6461.984084] usb 2-1: new full speed USB device using uhci_hcd and address 29
[ 6462.159301] usb 2-1: configuration #1 chosen from 1 choice
[ 6462.162412] scsi21 : SCSI emulation for USB Mass Storage devices
[ 6462.162698] usb-storage: device found at 29
[ 6462.162703] usb-storage: waiting for device to settle before scanning
[ 6467.161403] usb-storage: device scan complete
[ 6467.222378] scsi 21:0:0:0: Direct-Access              E870             1.00 PQ: 0 ANSI: 0 CCS
[ 6467.223560] sd 21:0:0:0: Attached scsi generic sg3 type 0
[ 6467.251345] sd 21:0:0:0: [sdb] 1984001 512-byte logical blocks: (1.01 GB/968 MiB)
[ 6467.258326] sd 21:0:0:0: [sdb] Write Protect is off
[ 6467.258345] sd 21:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6467.258352] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[ 6467.275524] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[ 6467.275557]  sdb: sdb1
[ 6467.305814] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[ 6467.305852] sd 21:0:0:0: [sdb] Attached SCSI removable disk
[ 6467.597846] sd 21:0:0:0: [sdb] Unhandled sense code
[ 6467.597864] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6467.597873] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6467.597884] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6467.597897] end_request: I/O error, dev sdb, sector 1984000
[ 6467.597914] Buffer I/O error on device sdb, logical block 1984000
[ 6467.620206] sd 21:0:0:0: [sdb] Unhandled sense code
[ 6467.620223] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6467.620231] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6467.620241] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6467.620255] end_request: I/O error, dev sdb, sector 1984000
[ 6467.620271] Buffer I/O error on device sdb, logical block 1984000
[ 6467.669191] sd 21:0:0:0: [sdb] Unhandled sense code
[ 6467.669208] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6467.669217] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6467.669227] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6467.669241] end_request: I/O error, dev sdb, sector 1984000
[ 6467.669257] Buffer I/O error on device sdb, logical block 1984000
[ 6467.691181] sd 21:0:0:0: [sdb] Unhandled sense code
[ 6467.691199] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6467.691207] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6467.691218] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6467.691231] end_request: I/O error, dev sdb, sector 1984000
[ 6467.691249] Buffer I/O error on device sdb, logical block 1984000
[ 6467.713175] sd 21:0:0:0: [sdb] Unhandled sense code
[ 6467.713193] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6467.713201] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6467.713213] sd 21:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 6467.713227] end_request: I/O error, dev sdb, sector 1984000
[ 6467.713241] Buffer I/O error on device sdb, logical block 1984000
[ 6467.760539] sd 21:0:0:0: [sdb] Unhandled sense code
[ 6467.760556] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6467.760564] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6467.760574] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6467.760588] end_request: I/O error, dev sdb, sector 1984000
[ 6467.760605] Buffer I/O error on device sdb, logical block 1984000
[ 6467.783949] sd 21:0:0:0: [sdb] Unhandled sense code
[ 6467.783967] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6467.783975] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6467.783986] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6467.783999] end_request: I/O error, dev sdb, sector 1984000
[ 6467.784054] Buffer I/O error on device sdb, logical block 1984000
[ 6480.904096] usb 2-1: USB disconnect, address 29
[ 6483.220068] usb 2-1: new full speed USB device using uhci_hcd and address 30
[ 6483.389630] usb 2-1: configuration #1 chosen from 1 choice
[ 6491.890055] scsi22 : SCSI emulation for USB Mass Storage devices
[ 6491.890583] usb-storage: device found at 30
[ 6491.890589] usb-storage: waiting for device to settle before scanning
[ 6493.304101] usb 2-1: USB disconnect, address 30
[ 6496.052036] usb 2-1: new full speed USB device using uhci_hcd and address 31
[ 6496.222520] usb 2-1: configuration #1 chosen from 1 choice
[ 6496.224808] scsi23 : SCSI emulation for USB Mass Storage devices
[ 6496.225080] usb-storage: device found at 31
[ 6496.225085] usb-storage: waiting for device to settle before scanning
[ 6501.225654] usb-storage: device scan complete
[ 6501.284584] scsi 23:0:0:0: Direct-Access              E870             1.00 PQ: 0 ANSI: 0 CCS
[ 6501.285792] sd 23:0:0:0: Attached scsi generic sg3 type 0
[ 6501.320853] sd 23:0:0:0: [sdb] 1984001 512-byte logical blocks: (1.01 GB/968 MiB)
[ 6501.330536] sd 23:0:0:0: [sdb] Write Protect is off
[ 6501.330554] sd 23:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6501.330561] sd 23:0:0:0: [sdb] Assuming drive cache: write through
[ 6501.346450] sd 23:0:0:0: [sdb] Assuming drive cache: write through
[ 6501.346475]  sdb: sdb1
[ 6501.386542] sd 23:0:0:0: [sdb] Assuming drive cache: write through
[ 6501.386567] sd 23:0:0:0: [sdb] Attached SCSI removable disk
[ 6501.587517] sd 23:0:0:0: [sdb] Unhandled sense code
[ 6501.587535] sd 23:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6501.587544] sd 23:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6501.587554] sd 23:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6501.587568] end_request: I/O error, dev sdb, sector 1984000
[ 6501.587584] Buffer I/O error on device sdb, logical block 1984000
[ 6501.609447] sd 23:0:0:0: [sdb] Unhandled sense code
[ 6501.609466] sd 23:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6501.609474] sd 23:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6501.609485] sd 23:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6501.609500] end_request: I/O error, dev sdb, sector 1984000
[ 6501.609517] Buffer I/O error on device sdb, logical block 1984000
[ 6501.663477] sd 23:0:0:0: [sdb] Unhandled sense code
[ 6501.663494] sd 23:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6501.663503] sd 23:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6501.663513] sd 23:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6501.663526] end_request: I/O error, dev sdb, sector 1984000
[ 6501.663544] Buffer I/O error on device sdb, logical block 1984000
[ 6501.687744] sd 23:0:0:0: [sdb] Unhandled sense code
[ 6501.687762] sd 23:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6501.687771] sd 23:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6501.687781] sd 23:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6501.687795] end_request: I/O error, dev sdb, sector 1984000
[ 6501.687813] Buffer I/O error on device sdb, logical block 1984000
[ 6501.711193] sd 23:0:0:0: [sdb] Unhandled sense code
[ 6501.711212] sd 23:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6501.711220] sd 23:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6501.711231] sd 23:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 6501.711246] end_request: I/O error, dev sdb, sector 1984000
[ 6501.711264] Buffer I/O error on device sdb, logical block 1984000
[ 6501.757410] sd 23:0:0:0: [sdb] Unhandled sense code
[ 6501.757426] sd 23:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6501.757434] sd 23:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6501.757443] sd 23:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6501.757456] end_request: I/O error, dev sdb, sector 1984000
[ 6501.757471] Buffer I/O error on device sdb, logical block 1984000
[ 6501.779422] sd 23:0:0:0: [sdb] Unhandled sense code
[ 6501.779439] sd 23:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6501.779448] sd 23:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 6501.779459] sd 23:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 6501.779473] end_request: I/O error, dev sdb, sector 1984000
[ 6501.779490] Buffer I/O error on device sdb, logical block 1984000
[ 6850.660241] sd 23:0:0:0: [sdb] Unhandled error code
[ 6850.660255] sd 23:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 6850.660264] end_request: I/O error, dev sdb, sector 1469600
[ 6850.660412] sd 23:0:0:0: [sdb] Unhandled error code
[ 6850.660417] sd 23:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 6850.660423] end_request: I/O error, dev sdb, sector 1469840
[ 6850.660514] sd 23:0:0:0: [sdb] Unhandled error code
[ 6850.660519] sd 23:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 6850.660525] end_request: I/O error, dev sdb, sector 1469856
[ 6850.660615] sd 23:0:0:0: [sdb] Unhandled error code
[ 6850.660620] sd 23:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 6850.660626] end_request: I/O error, dev sdb, sector 1470096
[ 6850.660699] usb 2-1: USB disconnect, address 31
[ 7652.560068] usb 2-1: new full speed USB device using uhci_hcd and address 32
[ 7652.730298] usb 2-1: configuration #1 chosen from 1 choice
[ 7652.733339] scsi24 : SCSI emulation for USB Mass Storage devices
[ 7652.733627] usb-storage: device found at 32
[ 7652.733632] usb-storage: waiting for device to settle before scanning
[ 7657.733379] usb-storage: device scan complete
[ 7657.794372] scsi 24:0:0:0: Direct-Access              E870             1.00 PQ: 0 ANSI: 0 CCS
[ 7657.795600] sd 24:0:0:0: Attached scsi generic sg3 type 0
[ 7657.811241] sd 24:0:0:0: [sdb] 1984001 512-byte logical blocks: (1.01 GB/968 MiB)
[ 7657.816270] sd 24:0:0:0: [sdb] Write Protect is off
[ 7657.816285] sd 24:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 7657.816292] sd 24:0:0:0: [sdb] Assuming drive cache: write through
[ 7657.833319] sd 24:0:0:0: [sdb] Assuming drive cache: write through
[ 7657.833352]  sdb: sdb1
[ 7657.853254] sd 24:0:0:0: [sdb] Assuming drive cache: write through
[ 7657.853276] sd 24:0:0:0: [sdb] Attached SCSI removable disk
[ 7659.464052] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7659.464071] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7659.464081] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7659.464091] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7659.464105] end_request: I/O error, dev sdb, sector 1984000
[ 7659.464124] Buffer I/O error on device sdb, logical block 1984000
[ 7659.487993] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7659.488042] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7659.488052] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7659.488063] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7659.488076] end_request: I/O error, dev sdb, sector 1984000
[ 7659.488093] Buffer I/O error on device sdb, logical block 1984000
[ 7659.570034] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7659.570052] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7659.570060] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7659.570071] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7659.570084] end_request: I/O error, dev sdb, sector 1984000
[ 7659.570101] Buffer I/O error on device sdb, logical block 1984000
[ 7659.601338] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7659.601357] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7659.601366] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7659.601377] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7659.601391] end_request: I/O error, dev sdb, sector 1984000
[ 7659.601408] Buffer I/O error on device sdb, logical block 1984000
[ 7659.623973] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7659.624035] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7659.624045] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7659.624056] sd 24:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 7659.624071] end_request: I/O error, dev sdb, sector 1984000
[ 7659.624087] Buffer I/O error on device sdb, logical block 1984000
[ 7659.670950] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7659.670968] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7659.670976] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7659.670987] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7659.671001] end_request: I/O error, dev sdb, sector 1984000
[ 7659.671017] Buffer I/O error on device sdb, logical block 1984000
[ 7659.692953] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7659.692972] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7659.692980] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7659.692997] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7659.693012] end_request: I/O error, dev sdb, sector 1984000
[ 7659.693028] Buffer I/O error on device sdb, logical block 1984000
[ 7662.339553] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7662.339572] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7662.339580] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7662.339591] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7662.339606] end_request: I/O error, dev sdb, sector 1984000
[ 7662.339674] Buffer I/O error on device sdb, logical block 1984000
[ 7662.361544] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7662.361563] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7662.361571] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7662.361581] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7662.361595] end_request: I/O error, dev sdb, sector 1984000
[ 7662.361611] Buffer I/O error on device sdb, logical block 1984000
[ 7662.421017] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7662.421037] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7662.421046] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7662.421057] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7662.421071] end_request: I/O error, dev sdb, sector 1984000
[ 7662.421089] Buffer I/O error on device sdb, logical block 1984000
[ 7662.447530] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7662.447548] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7662.447556] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7662.447566] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7662.447580] end_request: I/O error, dev sdb, sector 1984000
[ 7662.469487] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7662.469501] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7662.469508] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7662.469517] sd 24:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 7662.469530] end_request: I/O error, dev sdb, sector 1984000
[ 7662.512498] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7662.512514] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7662.512523] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7662.512534] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7662.512547] end_request: I/O error, dev sdb, sector 1984000
[ 7662.534499] sd 24:0:0:0: [sdb] Unhandled sense code
[ 7662.534517] sd 24:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7662.534525] sd 24:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7662.534536] sd 24:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7662.534549] end_request: I/O error, dev sdb, sector 1984000
[ 7669.568104] usb 2-1: USB disconnect, address 32
[ 7673.756072] usb 2-1: new full speed USB device using uhci_hcd and address 33
[ 7673.942312] usb 2-1: configuration #1 chosen from 1 choice
[ 7686.260365] scsi25 : SCSI emulation for USB Mass Storage devices
[ 7686.260759] usb 2-1: USB disconnect, address 33
[ 7686.260851] usb-storage: device found at 33
[ 7686.260855] usb-storage: waiting for device to settle before scanning
[ 7686.560069] usb 2-1: new full speed USB device using uhci_hcd and address 34
[ 7686.732275] usb 2-1: configuration #1 chosen from 1 choice
[ 7686.735320] scsi26 : SCSI emulation for USB Mass Storage devices
[ 7686.735598] usb-storage: device found at 34
[ 7686.735603] usb-storage: waiting for device to settle before scanning
[ 7692.880106] usb 2-1: USB disconnect, address 34
[ 7700.149013] usb-storage: device scan complete
[ 7734.892069] usb 2-1: new full speed USB device using uhci_hcd and address 35
[ 7739.052108] hub 2-0:1.0: unable to enumerate USB device on port 1
[ 7757.220174] usb 2-1: new full speed USB device using uhci_hcd and address 36
[ 7757.385610] usb 2-1: configuration #1 chosen from 1 choice
[ 7757.387701] scsi27 : SCSI emulation for USB Mass Storage devices
[ 7757.387955] usb-storage: device found at 36
[ 7757.387959] usb-storage: waiting for device to settle before scanning
[ 7761.824098] usb 2-1: USB disconnect, address 36
[ 7764.188073] usb 2-1: new full speed USB device using uhci_hcd and address 37
[ 7764.358539] usb 2-1: configuration #1 chosen from 1 choice
[ 7764.360893] scsi28 : SCSI emulation for USB Mass Storage devices
[ 7764.361222] usb-storage: device found at 37
[ 7764.361227] usb-storage: waiting for device to settle before scanning
[ 7769.372684] usb-storage: device scan complete
[ 7769.434757] scsi 28:0:0:0: Direct-Access              E870             1.00 PQ: 0 ANSI: 0 CCS
[ 7769.435936] sd 28:0:0:0: Attached scsi generic sg3 type 0
[ 7769.473036] sd 28:0:0:0: [sdb] 1984001 512-byte logical blocks: (1.01 GB/968 MiB)
[ 7769.483567] sd 28:0:0:0: [sdb] Write Protect is off
[ 7769.483586] sd 28:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 7769.483593] sd 28:0:0:0: [sdb] Assuming drive cache: write through
[ 7769.510648] sd 28:0:0:0: [sdb] Assuming drive cache: write through
[ 7769.510678]  sdb: sdb1
[ 7769.548503] sd 28:0:0:0: [sdb] Assuming drive cache: write through
[ 7769.548529] sd 28:0:0:0: [sdb] Attached SCSI removable disk
[ 7769.800447] sd 28:0:0:0: [sdb] Unhandled sense code
[ 7769.800479] sd 28:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7769.800488] sd 28:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7769.800499] sd 28:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7769.800512] end_request: I/O error, dev sdb, sector 1984000
[ 7769.800527] __ratelimit: 4 callbacks suppressed
[ 7769.800534] Buffer I/O error on device sdb, logical block 1984000
[ 7769.822422] sd 28:0:0:0: [sdb] Unhandled sense code
[ 7769.822439] sd 28:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7769.822448] sd 28:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7769.822458] sd 28:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7769.822472] end_request: I/O error, dev sdb, sector 1984000
[ 7769.822489] Buffer I/O error on device sdb, logical block 1984000
[ 7769.873410] sd 28:0:0:0: [sdb] Unhandled sense code
[ 7769.873427] sd 28:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7769.873436] sd 28:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7769.873446] sd 28:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7769.873460] end_request: I/O error, dev sdb, sector 1984000
[ 7769.873477] Buffer I/O error on device sdb, logical block 1984000
[ 7769.896446] sd 28:0:0:0: [sdb] Unhandled sense code
[ 7769.896463] sd 28:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7769.896472] sd 28:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7769.896482] sd 28:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7769.896495] end_request: I/O error, dev sdb, sector 1984000
[ 7769.896512] Buffer I/O error on device sdb, logical block 1984000
[ 7769.918412] sd 28:0:0:0: [sdb] Unhandled sense code
[ 7769.918430] sd 28:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7769.918438] sd 28:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7769.918448] sd 28:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 7769.918463] end_request: I/O error, dev sdb, sector 1984000
[ 7769.918479] Buffer I/O error on device sdb, logical block 1984000
[ 7769.963404] sd 28:0:0:0: [sdb] Unhandled sense code
[ 7769.963422] sd 28:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7769.963430] sd 28:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7769.963441] sd 28:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7769.963454] end_request: I/O error, dev sdb, sector 1984000
[ 7769.963472] Buffer I/O error on device sdb, logical block 1984000
[ 7770.000874] sd 28:0:0:0: [sdb] Unhandled sense code
[ 7770.000891] sd 28:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7770.000899] sd 28:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7770.000909] sd 28:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7770.000924] end_request: I/O error, dev sdb, sector 1984000
[ 7770.000941] Buffer I/O error on device sdb, logical block 1984000
[ 7781.168103] usb 2-1: USB disconnect, address 37
[ 7803.388068] usb 2-1: new full speed USB device using uhci_hcd and address 38
[ 7803.559312] usb 2-1: configuration #1 chosen from 1 choice
[ 7803.912989] scsi29 : SCSI emulation for USB Mass Storage devices
[ 7803.925094] usb-storage: device found at 38
[ 7803.925105] usb-storage: waiting for device to settle before scanning
[ 7808.925371] usb-storage: device scan complete
[ 7808.984345] scsi 29:0:0:0: Direct-Access              E870             1.00 PQ: 0 ANSI: 0 CCS
[ 7808.985547] sd 29:0:0:0: Attached scsi generic sg3 type 0
[ 7809.018666] sd 29:0:0:0: [sdb] 1984001 512-byte logical blocks: (1.01 GB/968 MiB)
[ 7809.027946] sd 29:0:0:0: [sdb] Write Protect is off
[ 7809.027965] sd 29:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 7809.027971] sd 29:0:0:0: [sdb] Assuming drive cache: write through
[ 7809.050260] sd 29:0:0:0: [sdb] Assuming drive cache: write through
[ 7809.050290]  sdb: sdb1
[ 7809.083261] sd 29:0:0:0: [sdb] Assuming drive cache: write through
[ 7809.083290] sd 29:0:0:0: [sdb] Attached SCSI removable disk
[ 7809.293177] sd 29:0:0:0: [sdb] Unhandled sense code
[ 7809.293195] sd 29:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7809.293203] sd 29:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7809.293214] sd 29:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7809.293227] end_request: I/O error, dev sdb, sector 1984000
[ 7809.293244] Buffer I/O error on device sdb, logical block 1984000
[ 7809.315168] sd 29:0:0:0: [sdb] Unhandled sense code
[ 7809.315186] sd 29:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7809.315195] sd 29:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7809.315205] sd 29:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7809.315218] end_request: I/O error, dev sdb, sector 1984000
[ 7809.315234] Buffer I/O error on device sdb, logical block 1984000
[ 7809.365165] sd 29:0:0:0: [sdb] Unhandled sense code
[ 7809.365184] sd 29:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7809.365198] sd 29:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7809.365209] sd 29:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7809.365223] end_request: I/O error, dev sdb, sector 1984000
[ 7809.365239] Buffer I/O error on device sdb, logical block 1984000
[ 7809.387160] sd 29:0:0:0: [sdb] Unhandled sense code
[ 7809.387179] sd 29:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7809.387187] sd 29:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7809.387198] sd 29:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7809.387211] end_request: I/O error, dev sdb, sector 1984000
[ 7809.387227] Buffer I/O error on device sdb, logical block 1984000
[ 7809.410520] sd 29:0:0:0: [sdb] Unhandled sense code
[ 7809.410539] sd 29:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7809.410547] sd 29:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7809.410557] sd 29:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 7809.410572] end_request: I/O error, dev sdb, sector 1984000
[ 7809.410588] Buffer I/O error on device sdb, logical block 1984000
[ 7809.455174] sd 29:0:0:0: [sdb] Unhandled sense code
[ 7809.455192] sd 29:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7809.455201] sd 29:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7809.455211] sd 29:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7809.455225] end_request: I/O error, dev sdb, sector 1984000
[ 7809.455241] Buffer I/O error on device sdb, logical block 1984000
[ 7809.477148] sd 29:0:0:0: [sdb] Unhandled sense code
[ 7809.477167] sd 29:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7809.477175] sd 29:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 7809.477185] sd 29:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 7809.477199] end_request: I/O error, dev sdb, sector 1984000
[ 7809.477217] Buffer I/O error on device sdb, logical block 1984000
[ 7863.252807] usb 2-1: USB disconnect, address 38
[ 7865.273532] FAT: Directory bread(block 487) failed
[ 7865.273613] FAT: Directory bread(block 488) failed
[ 7865.273633] FAT: Directory bread(block 489) failed
[ 7865.273652] FAT: Directory bread(block 490) failed
[ 7865.273671] FAT: Directory bread(block 491) failed
[ 7865.273690] FAT: Directory bread(block 492) failed
[ 7865.273710] FAT: Directory bread(block 493) failed
[ 7865.273729] FAT: Directory bread(block 494) failed
[ 7865.273748] FAT: Directory bread(block 495) failed
[ 7865.273774] FAT: Directory bread(block 496) failed
[ 7865.273794] FAT: Directory bread(block 497) failed
[ 7865.273812] FAT: Directory bread(block 498) failed
[ 7865.273831] FAT: Directory bread(block 499) failed
[ 7865.273850] FAT: Directory bread(block 500) failed
[ 7865.273869] FAT: Directory bread(block 501) failed
[ 7865.273888] FAT: Directory bread(block 502) failed
[ 7865.273907] FAT: Directory bread(block 503) failed
[ 7865.273933] FAT: Directory bread(block 504) failed
[ 7865.273952] FAT: Directory bread(block 505) failed
[ 7865.273971] FAT: Directory bread(block 506) failed
[ 7865.273990] FAT: Directory bread(block 507) failed
[ 7865.274009] FAT: Directory bread(block 508) failed
[ 7865.274028] FAT: Directory bread(block 509) failed
[ 7865.274046] FAT: Directory bread(block 510) failed
[ 7865.274065] FAT: Directory bread(block 511) failed
[ 7865.274116] FAT: Directory bread(block 512) failed
[ 7865.274135] FAT: Directory bread(block 513) failed
[ 7865.274154] FAT: Directory bread(block 514) failed
[ 7865.274173] FAT: Directory bread(block 515) failed
[ 7865.274192] FAT: Directory bread(block 516) failed
[ 7865.274211] FAT: Directory bread(block 517) failed
[ 7865.274229] FAT: Directory bread(block 518) failed
[ 7906.532076] usb 2-2: new full speed USB device using uhci_hcd and address 39
[ 7906.717291] usb 2-2: configuration #1 chosen from 1 choice
[ 7906.721303] uvcvideo: Found UVC 1.00 device USB 2.0 PC Cam (090c:b371)
[ 7906.824463] input: USB 2.0 PC Cam as /devices/pci0000:00/0000:00:1f.4/usb2/2-2/2-2:1.0/input/input9
[ 7962.427296] uvcvideo: Non-zero status (-84) in status completion handler.
[ 7962.460622] hub 2-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 7962.460645] usb 2-2: USB disconnect, address 39
[ 7962.704937] usb 2-2: new full speed USB device using uhci_hcd and address 40
[ 7962.897536] usb 2-2: configuration #1 chosen from 1 choice
[ 7962.900577] uvcvideo: Found UVC 1.00 device USB 2.0 PC Cam (090c:b371)
[ 7962.921130] input: USB 2.0 PC Cam as /devices/pci0000:00/0000:00:1f.4/usb2/2-2/2-2:1.0/input/input10
[ 7968.160182] hub 2-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 7968.160202] usb 2-2: USB disconnect, address 40
[ 7968.404083] usb 2-2: new full speed USB device using uhci_hcd and address 41
[ 7968.604431] usb 2-2: configuration #1 chosen from 1 choice
[ 7968.608654] uvcvideo: Found UVC 1.00 device USB 2.0 PC Cam (090c:b371)
[ 7968.614246] input: USB 2.0 PC Cam as /devices/pci0000:00/0000:00:1f.4/usb2/2-2/2-2:1.0/input/input11
[ 7982.544104] usb 2-2: USB disconnect, address 41
[ 7983.280080] usb 2-2: new full speed USB device using uhci_hcd and address 42
[ 7983.465306] usb 2-2: configuration #1 chosen from 1 choice
[ 7983.469464] uvcvideo: Found UVC 1.00 device USB 2.0 PC Cam (090c:b371)
[ 7983.898596] input: USB 2.0 PC Cam as /devices/pci0000:00/0000:00:1f.4/usb2/2-2/2-2:1.0/input/input12
[ 8255.344234] hub 2-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 8255.344257] usb 2-2: USB disconnect, address 42
[ 8255.592536] usb 2-2: new full speed USB device using uhci_hcd and address 43
[ 8255.806956] usb 2-2: configuration #1 chosen from 1 choice
[ 8255.810736] uvcvideo: Found UVC 1.00 device USB 2.0 PC Cam (090c:b371)
[ 8255.816100] input: USB 2.0 PC Cam as /devices/pci0000:00/0000:00:1f.4/usb2/2-2/2-2:1.0/input/input13
[ 8259.628812] uvcvideo: Non-zero status (-84) in status completion handler.
[ 8259.808111] hub 2-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 8259.808129] usb 2-2: USB disconnect, address 43
[ 8260.052046] usb 2-2: new full speed USB device using uhci_hcd and address 44
[ 8260.237003] usb 2-2: configuration #1 chosen from 1 choice
[ 8260.241234] uvcvideo: Found UVC 1.00 device USB 2.0 PC Cam (090c:b371)
[ 8260.264410] input: USB 2.0 PC Cam as /devices/pci0000:00/0000:00:1f.4/usb2/2-2/2-2:1.0/input/input14


^Bump^

---

### Post by J V on 2010-01-02
1: edits don't bump
2: there are a LOT of errors there... Absolute beginners talk is out of this depth lol :/
3: It recognizes your camera... thats not the problem...

---

### Post by vvfrn on 2010-01-02
> **J V said:**
> 1: edits don't bump
2: there are a LOT of errors there... Absolute beginners talk is out of this depth lol :/
3: It recognizes your camera... thats not the problem...

1. Thanks(I never knew that)!
2,3. I do not understand if it is detected why doesn't it show in the My computer page and why does it not play with Cameroid.com or Cheese(a standalone webcam program). And the errors can also be from other digital camera which sometimes connects or fails to connect.
**Does anyone know why its not working?I need it for my online class!**
^Bump^

---

### Post by Methuselah on 2010-01-02
The cam seems to be recognized and associated with the uvcvideo driver which is supposed to support it.

All I can say is to try cheese again...edit->preferences and see if you can select another device.

---

### Post by spiderbatdad on 2010-01-02
[http://blog.larsstrand.org//article.php?story=Linux_and_LogitechQuickCamPro9000](http://blog.larsstrand.org//article.php?story=Linux_and_LogitechQuickCamPro9000)

[http://ubuntuforums.org/showthread.php?t=913832](http://ubuntuforums.org/showthread.php?t=913832)

---

