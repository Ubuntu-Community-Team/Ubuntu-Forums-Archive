---
title: "Lucid crashes Blackberry Storm"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by rtlustyo on 2010-07-19
Pretty simple, when I plug my storm in it crashes, showing a java error or something on the phone. My kernel is 2.6.32-23-generic on X86_64. This is the dmesg output, 

[19124.884173] Initializing USB Mass Storage driver...
[19124.884436] scsi3 : SCSI emulation for USB Mass Storage devices
[19124.885184] usbcore: registered new interface driver usb-storage
[19124.885193] USB Mass Storage support registered.
[19124.889699] usb-storage: device found at 3
[19124.889706] usb-storage: waiting for device to settle before scanning
[19129.883316] usb-storage: device scan complete
[19129.884891] scsi 3:0:0:0: Direct-Access     RIM      BlackBerry SD    0003 PQ: 0 ANSI: 4 CCS
[19129.886270] scsi 3:0:0:1: Direct-Access     RIM      BlackBerry       1003 PQ: 0 ANSI: 4 CCS
[19129.890901] sd 3:0:0:0: Attached scsi generic sg2 type 0
[19129.891454] sd 3:0:0:1: Attached scsi generic sg3 type 0
[19129.902270] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[19129.903458] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[19129.941366] usb 1-6: USB disconnect, address 3
[19130.290261] usb 1-6: new high speed USB device using ehci_hcd and address 4
[19130.432803] usb 1-6: configuration #1 chosen from 1 choice
[19130.436865] scsi4 : SCSI emulation for USB Mass Storage devices
[19130.437241] usb-storage: device found at 4
[19130.437246] usb-storage: waiting for device to settle before scanning
[19132.090328] usb 1-6: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 170 len 1000 ret -110
[19132.233204] usb 1-6: USB disconnect, address 4
[19132.237046] usb 1-6: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 128 rq 6 len 255 ret -108
[19135.080284] usb 4-3: new full speed USB device using ohci_hcd and address 2
[19135.281999] usb 4-3: configuration #1 chosen from 1 choice
[19135.309019] usbcore: registered new interface driver berry_charge
[19152.237833] usb 4-3: USB disconnect, address 2

Any help would be appreciated, thanks!

---

### Post by erbey on 2010-07-20
Hi i also have the exact same problem, full newbie to linux and programming but saying your not the only one with this problem, i have a storm 9500 if it  helps anyone?

---

### Post by erbey on 2010-07-27
[http://ubuntuforums.org/showthread.php?t=1431784&highlight=blackberry+storm&page=2](http://ubuntuforums.org/showthread.php?t=1431784&highlight=blackberry+storm&page=2)
this thread has apparently found a temporary fix 
sudo mv /lib/udev/rules.d/85-hdparm.rules  /lib/udev/rules.d/85-hdparm.rules.disabled
although this hasn't worked for everyone (me)
although hopefully it helps you

---

### Post by rtlustyo on 2010-08-12
yea I tried opensync-plugin-barry and sudo mv /lib/udev/rules.d/85-hdparm.rules /lib/udev/rules.d/85-hdparm.rules.disabled, still nothing. Thanks for the help though. Anyone else?

---

