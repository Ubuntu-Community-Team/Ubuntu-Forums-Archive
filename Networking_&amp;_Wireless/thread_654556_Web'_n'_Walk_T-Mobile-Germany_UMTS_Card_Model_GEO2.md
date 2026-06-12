---
title: "Web' n' Walk T-Mobile-Germany UMTS Card Model: GEO201 will not work"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by WebBuddha on 2007-12-31
hi there,

i'm getting crazy with my tries of getting the UMTS card running on ubuntu 7.10.
I've read different how-to's on this but I'm getting stucked, so I'm hopefull to get your help on my issue.

I've got follow infos at the moment.
UMTS Card Option Model: GEO201 
SNR: FE3873XXXX
FCC ID: NCM0GEO201

I run follow command's already:

lsusb
> Bus 004 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 003 Device 002: ID 05c6:1000 Qualcomm, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

dmesg
> [ 2683.544000] Initializing USB Mass Storage driver...
[ 2683.544000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 2683.544000] usb-storage: device found at 2
[ 2683.544000] usb-storage: waiting for device to settle before scanning
[ 2683.544000] usbcore: registered new interface driver usb-storage
[ 2683.544000] USB Mass Storage support registered.
[ 2688.544000] usb-storage: device scan complete
[ 2688.548000] scsi 5:0:0:0: CD-ROM GT HSDPA Modem 3.00 PQ: 0 ANSI: 2
[ 2688.580000] sr1: scsi-1 drive
[ 2688.580000] sr 5:0:0:0: Attached scsi CD-ROM sr1
[ 2688.580000] sr 5:0:0:0: Attached scsi generic sg2 type 5
[ 2689.212000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2689.216000] ISOFS: changing to secondary root

This is what I've found in /var/log/messages
> Dec 31 10:51:00 lappy kernel: [ 668.348000] usb 1-2: new full speed USB device using uhci_hcd and address 3
Dec 31 10:51:00 lappy kernel: [ 668.512000] usb 1-2: configuration #1 chosen from 1 choice
Dec 31 10:51:00 lappy kernel: [ 668.516000] scsi6 : SCSI emulation for USB Mass Storage devices
Dec 31 10:51:05 lappy kernel: [ 673.524000] scsi 6:0:0:0: CD-ROM GT HSDPA Modem 3.00 PQ: 0 ANSI: 2
Dec 31 10:51:05 lappy kernel: [ 673.556000] sr1: scsi-1 drive
Dec 31 10:51:05 lappy kernel: [ 673.556000] sr 6:0:0:0: Attached scsi generic sg2 type 5

So it looks like that my UMTS Card will be recognized as CD-ROM.

Regards
WebBuddha


BTW: Sorry for my broken english

---

### Post by WebBuddha on 2008-01-01
nobody here who is able to help me on this issue?

Regards
WebBuddha

---

