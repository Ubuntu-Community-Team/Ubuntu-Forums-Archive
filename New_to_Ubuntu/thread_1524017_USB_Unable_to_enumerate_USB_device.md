---
title: "USB Unable to enumerate USB device"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by cwmoser on 2010-07-04
When I plug in my Olympus USB camera cable, it won't mount.  When I run dmesg command I note the following:

[COLOR="Navy"][SIZE="2"][118307.010132] usb 1-6: new high speed USB device using ehci_hcd and address 6
[118322.130051] usb 1-6: device descriptor read/64, error -110
[118322.320126] hub 1-0:1.0: unable to enumerate USB device on port 6
[118776.130045] usb 1-5: reset high speed USB device using ehci_hcd and address 3[/SIZE][/COLOR]

Apparently there is something about how Ubuntu handles USB ports.

Any ideas on how to fix this?

Thanks

Carl
cwmoser

---

### Post by J V on 2010-07-04
Try this and see if it works...
```
rmmod ehci_hcd
```

---

### Post by cwmoser on 2010-07-04
When I issue **rmmod echi_hcd**, I get:

[COLOR="Blue"]ERROR:  Module ehci_hcd does not exist in /proc/modules[/COLOR]

---

### Post by J V on 2010-07-04
Then nope, I have no idea :S

---

### Post by cwmoser on 2010-07-04
Here is what dmesg shows after I connected the USB camera:
[COLOR="Blue"][SIZE="2"]
[120383.010052] usb 1-6: new high speed USB device using ehci_hcd and address 9
[120383.161718] usb 1-6: configuration #1 chosen from 1 choice
[120383.162282] scsi9 : SCSI emulation for USB Mass Storage devices
[120383.162648] usb-storage: device found at 9
[120383.162652] usb-storage: waiting for device to settle before scanning
[120388.160369] usb-storage: device scan complete
[120388.160942] scsi 9:0:0:0: Direct-Access     OLYMPUS  FE280/X820/C520  1.00 PQ: 0 ANSI: 2
[120388.163750] sd 9:0:0:0: Attached scsi generic sg9 type 0
[120388.171558] sd 9:0:0:0: [sdi] 4095630 512-byte logical blocks: (2.09 GB/1.95 GiB)
[120388.174814] sd 9:0:0:0: [sdi] Write Protect is off
[120388.174826] sd 9:0:0:0: [sdi] Mode Sense: 18 00 00 08
[120388.174831] sd 9:0:0:0: [sdi] Assuming drive cache: write through
[120388.180910] sd 9:0:0:0: [sdi] Assuming drive cache: write through
[120388.180922]  sdi: sdi1
[120388.193663] sd 9:0:0:0: [sdi] Assuming drive cache: write through
[120388.193674] sd 9:0:0:0: [sdi] Attached SCSI removable disk
[120391.350039] usb 1-6: reset high speed USB device using ehci_hcd and address 9
[120391.430085] usb 1-6: USB disconnect, address 9
[120391.430417] sd 9:0:0:0: [sdi] Unhandled error code
[120391.430423] sd 9:0:0:0: [sdi] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[120391.430431] sd 9:0:0:0: [sdi] CDB: Read(10): 28 00 00 00 08 00 00 00 08 00
[120391.430449] end_request: I/O error, dev sdi, sector 2048
[120391.430459] Buffer I/O error on device sdi, logical block 1024
[120391.430467] Buffer I/O error on device sdi, logical block 1025
[120391.430473] Buffer I/O error on device sdi, logical block 1026
[120391.430480] Buffer I/O error on device sdi, logical block 1027
[120391.585074] usb 1-6: new high speed USB device using ehci_hcd and address 10
[120391.660091] hub 1-0:1.0: unable to enumerate USB device on port 6[/SIZE][/COLOR]


Carl

---

