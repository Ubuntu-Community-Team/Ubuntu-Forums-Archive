---
title: "Nokia 6681 and Dongle Bluetooth adapter"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by daniloeu on 2006-11-30
Hi everbody!

I buy a phone (Nokia 6681) yesterday and I'm having some problems with the dongle that was come with the phone...

The problem is that: Ubuntu can not recognize the dongle...
 
My Dmesg say me this:
```

[17464240.868000] usb 5-1: new high speed USB device using ehci_hcd and address 16
[17464241.004000] usb 5-1: configuration #1 chosen from 1 choice
[17464241.004000] scsi7 : SCSI emulation for USB Mass Storage devices
[17464241.004000] usb-storage: device found at 16
[17464241.004000] usb-storage: waiting for device to settle before scanning
[17464246.004000] usb-storage: device scan complete
[17464246.004000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9228
[17464246.004000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17464246.008000] sd 7:0:0:0: Attached scsi removable disk sda
[17464246.008000] sd 7:0:0:0: Attached scsi generic sg0 type 0
```

Really strange.... =P
I think that Ubutu is thinking that my BTDongle is a storage device.... But is not... lol \0/

My lsusb return this:
```

Bus 005 Device 016: ID 05e3:0712 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 002 Device 001: ID 0000:000

```


So, someone can give-me a idea to fix this problem? Or a reference to found a solution? (yes, I had look at google but I did not found any references).

I dont know chipset of this dongle... behind of it is write:

NOKIA             Type: DD-10
1601005771

---

