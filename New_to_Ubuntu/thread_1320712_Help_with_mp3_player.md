---
title: "Help with mp3 player"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by helius0 on 2009-11-09
I've got a Chinese PMP (RAmos T11 RK) that works just fine under Windows XP, where it shows up as a removable hard drive.  However, Ubuntu 9.10 just refuses to see it.  Can anyone help?

"lsusb" shows the device:
```
Bus 001 Device 046: ID 071b:3203 Domain Technologies, Inc. 

```"dmesg | tail" shows:
```
[85381.364158] usb 1-1: new high speed USB device using ehci_hcd and address 45
[85381.497060] usb 1-1: configuration #1 chosen from 1 choice
[85381.508316] scsi14 : SCSI emulation for USB Mass Storage devices
[85381.509928] usb-storage: device found at 45
[85381.509933] usb-storage: waiting for device to settle before scanning
[85381.532560] usb 1-1: USB disconnect, address 45
[85381.812073] usb 1-1: new high speed USB device using ehci_hcd and address 46
[85381.945059] usb 1-1: configuration #1 chosen from 1 choice
[85381.948357] scsi15 : SCSI emulation for USB Mass Storage devices
[85381.948720] usb-storage: device found at 46
[85381.948724] usb-storage: waiting for device to settle before scanning
[85386.949365] usb-storage: device scan complete
[85386.949947] scsi 15:0:0:0: Direct-Access     RK28XX   USB-MSC          1.00 PQ: 0 ANSI: 0
[85386.950428] scsi 15:0:0:1: Direct-Access     RK28XX   USB-MSC          1.00 PQ: 0 ANSI: 0
[85386.951290] sd 15:0:0:0: Attached scsi generic sg2 type 0
[85386.951493] sd 15:0:0:1: Attached scsi generic sg3 type 0
[85386.963272] sd 15:0:0:0: [sdb] 15106048 512-byte logical blocks: (7.73 GB/7.20 GiB)
[85386.968419] sd 15:0:0:1: [sdc] Attached SCSI removable disk
[85386.971876] sd 15:0:0:0: [sdb] Write Protect is off
[85386.971885] sd 15:0:0:0: [sdb] Mode Sense: 00 00 00 00
[85386.971891] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[85386.980642] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[85386.980649]  sdb:
[85417.101121] usb 1-1: reset high speed USB device using ehci_hcd and address 46
[85427.345119] usb 1-1: reset high speed USB device using ehci_hcd and address 46
[85432.591018] usb 1-1: reset high speed USB device using ehci_hcd and address 46
[85432.841119] usb 1-1: reset high speed USB device using ehci_hcd and address 46
[85432.973665] sd 15:0:0:0: Device offlined - not ready after error recovery
[85432.973686] sd 15:0:0:0: [sdb] Unhandled error code
[85432.973691] sd 15:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[85432.973699] end_request: I/O error, dev sdb, sector 0
[85432.973710] Buffer I/O error on device sdb, logical block 0
[85432.974865] sd 15:0:0:0: rejecting I/O to offline device
[85432.974904] sd 15:0:0:0: rejecting I/O to offline device
[85432.974926] sd 15:0:0:0: rejecting I/O to offline device
[85432.974945] sd 15:0:0:0: rejecting I/O to offline device
[85432.974958] ldm_validate_partition_table(): Disk read failed.
[85432.974970] sd 15:0:0:0: rejecting I/O to offline device
[85432.974988] sd 15:0:0:0: rejecting I/O to offline device
[85432.975006] sd 15:0:0:0: rejecting I/O to offline device
[85432.975029] sd 15:0:0:0: rejecting I/O to offline device
[85432.975041] Dev sdb: unable to read RDB block 0
[85432.975053] sd 15:0:0:0: rejecting I/O to offline device
[85432.975072] sd 15:0:0:0: rejecting I/O to offline device
[85432.975121] sd 15:0:0:0: rejecting I/O to offline device
[85432.975139] sd 15:0:0:0: rejecting I/O to offline device
[85432.975174] sd 15:0:0:0: rejecting I/O to offline device
[85432.975201] sd 15:0:0:0: rejecting I/O to offline device
[85432.975213]  unable to read partition table
[85432.975426] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[85433.100076] usb 1-1: reset high speed USB device using ehci_hcd and address 46
[85433.364306] usb 1-1: reset high speed USB device using ehci_hcd and address 46
[85433.616105] usb 1-1: reset high speed USB device using ehci_hcd and address 46

```And the "reset high speed USB device" keeps going indefinitely.

---

### Post by Chronon on 2009-11-09
Hi.  

[COLOR=Silver]There was a bug in Jaunty in which gphoto2 would interfere with (auto-)mounting of UMS devices by wrongly asserting that they were MTP.  I thought this was fixed, however, as I haven't had any problems with my 9.10 mounting various devices in MSC mode (both Kubuntu on desktop and Ubuntu on netbook).

Anyway, you could try to kill any gphoto2 related processes and then plug in your player and see if it gets auto-mounted.[/COLOR]

I don't think that's likely, actually.  It looks like some other bug as there seems to be some kind of improper recovery from an error.  I am not having any trouble with my UMS devices in 9.10, so maybe your player does something non-standard that's causing problems.  Hopefully somebody can drop by and give some better advice.

This appears to be the relevant bit from what I can tell:
```
[85432.973665] sd 15:0:0:0: Device offlined - not ready after error recovery
[85432.973686] sd 15:0:0:0: [sdb] Unhandled error code
[85432.973691] sd 15:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[85432.973699] end_request: I/O error, dev sdb, sector 0

```

Unfortunately, I can't make anything out beyond that.

---

### Post by helius0 on 2009-11-20
Help? Anyone (else)?  :frown:

Beuller?  Beuller?

---

### Post by canningtony16 on 2009-11-21
Sorry dont know much about this . I can only suggest u a technician.

---

### Post by commandant_gogo on 2009-12-01
Hi everyone,

got the same with my brand new Ramos T11RK with Karmic.

If it can helps when i plug it  my CPU is going 100% for 2mn then stop and Cairo-dock provides me the following message
> "RK28XX USB-MSC-1 is now unmounted"

I got the same command outputs as described by helius0

output for dmesg:
> [13416.593471] sd 18:0:0:0: [sdc] Unhandled error code
[13416.593476] sd 18:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[13416.593481] end_request: I/O error, dev sdc, sector 0
[13416.593487] Buffer I/O error on device sdc, logical block 0
[13416.593511]  unable to read partition table

[13431.816611] sd 18:0:0:0: [sdc] Attached SCSI removable disk
[13500.344518] usb 2-1: reset high speed USB device using ehci_hcd and address 17
...
[13500.412229] usb 2-1: USB disconnect, address 17
[13505.536017] usb 2-1: new high speed USB device using ehci_hcd and address 18
[13505.592304] hub 2-0:1.0: unable to enumerate USB device on port 1
[13505.860025] usb 2-1: new high speed USB device using ehci_hcd and address 19
[13505.993522] usb 2-1: configuration #1 chosen from 1 choice
[13505.994105] scsi19 : SCSI emulation for USB Mass Storage devices
[13505.994287] usb-storage: device found at 19
[13505.994290] usb-storage: waiting for device to settle before scanning

---

