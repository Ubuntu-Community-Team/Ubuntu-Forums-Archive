---
title: "Alcatel OneTouch x230 modem detected only if plugged in before booting"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by nikhilgeo on 2013-09-21
Hey,

*_My System Details._*

 **3G USB modem:-** Alcatel OneTouch x230
**Ubuntu:-** 13.04 fresh installation.

Before  booting the system if i plug in the USB modem the Modile Broadband  connection will come under Network Applet and i can connect and  everything works fine.
If i plug in the USB modem after i log into Ubuntu, the Network Applet shows no sign of my USB modem.

I have created a Mobile Broadband connection earlier from 'Edit Connection'.

Is this a bug..? 
Please suggest a way to make my system detect my USB modem when i plug it in anytime.

Regards
Nikhil

---

### Post by nikhilgeo on 2013-10-20
Below is what i get after giving: lsusb


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b354 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
[B]Bus 003 Device 004: ID 1bbb:f000 T & A Mobile Phones
[/B]
This is the output of: dmesg | tail -40

[ 3441.485962] usb 3-3: USB disconnect, device number 4
[ 3451.514476] usb 3-3: new high-speed USB device number 5 using xhci_hcd
[ 3451.533833] usb 3-3: New USB device found, idVendor=1bbb, idProduct=f000
[ 3451.533845] usb 3-3: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[ 3451.533851] usb 3-3: Product: HSPA Data Card
[ 3451.533856] usb 3-3: Manufacturer: USBModem
[ 3451.533861] usb 3-3: SerialNumber: 1234567890ABCDEF
[ 3451.536593] usb-storage 3-3:1.0: USB Mass Storage device detected
[ 3451.536875] scsi9 : usb-storage 3-3:1.0
[ 3452.535313] scsi 9:0:0:0: Direct-Access     ALCATEL  Mass Storage     2.31 PQ: 0 ANSI: 2
[ 3452.535972] scsi 9:0:0:1: CD-ROM            ALCATEL  Mass Storage     2.31 PQ: 0 ANSI: 2
[ 3452.536590] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 3452.539897] sr1: scsi-1 drive
[ 3452.540290] sr 9:0:0:1: Attached scsi CD-ROM sr1
[ 3452.540513] sr 9:0:0:1: Attached scsi generic sg3 type 5
[ 3452.541833] sd 9:0:0:0: [sdb] Attached SCSI removable disk


right now i have updated my system to 13.10.
Then also the same problem persist..
I would be helpful if anyone could suggest a solution for this problem

---

### Post by nikhilgeo on 2013-10-20
Have any one tried Alcatel on Ubuntu.?
Also i was wondering if there are any application where we can see the setting of the Datacard, send msg choose 3G/2G etc like the one supplied with this one for windows..?

---

