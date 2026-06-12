---
title: "prolink phs100 usb 3g dongle problem?"
date: 2014-12-26
forum: Networking &amp; Wireless
---

### Post by shamsat on 2014-12-26
Ubuntu 14.10 with kernel 3.16.0-28-generic is installed, when i insert the problink phs100 3g dongle in Dell i3 laptop, cannot get the usb ttyUSB* prots and get this error:

> 
Dec 26 14:27:03 user kernel: [  322.566309] usb 3-1: USB disconnect, device number 4
Dec 26 14:27:12 user kernel: [  332.022497] usb 3-2: new high-speed USB device number 5 using xhci_hcd
Dec 26 14:27:13 user kernel: [  332.210103] usb 3-2: New USB device found, idVendor=1e0e, idProduct=f000
Dec 26 14:27:13 user kernel: [  332.210111] usb 3-2: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Dec 26 14:27:13 user kernel: [  332.210115] usb 3-2: Product: PROLINK 
Dec 26 14:27:13 user kernel: [  332.210118] usb 3-2: Manufacturer: PROLINK 
Dec 26 14:27:13 user kernel: [  332.210121] usb 3-2: SerialNumber: 1234567890ABCDEF
Dec 26 14:27:13 user kernel: [  332.213291] usb-storage 3-2:1.0: USB Mass Storage device detected
Dec 26 14:27:13 user kernel: [  332.214660] scsi9 : usb-storage 3-2:1.0
Dec 26 14:27:13 user mtp-probe: checking bus 3, device 5: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2"
Dec 26 14:27:13 user mtp-probe: bus: 3, device: 5 was not an MTP device
Dec 26 14:27:14 user kernel: [  333.217433] scsi 9:0:0:0: CD-ROM            PROLINK  HSDPA Modem      2.31 PQ: 0 ANSI: 0
Dec 26 14:27:14 user kernel: [  333.222380] sr1: scsi-1 drive
Dec 26 14:27:14 user kernel: [  333.222751] sr 9:0:0:0: Attached scsi CD-ROM sr1
Dec 26 14:27:14 user kernel: [  333.223073] sr 9:0:0:0: Attached scsi generic sg3 type 5
Dec 26 14:27:14 user usb_modeswitch: switch device 1e0e:f000 on 003/005
Dec 26 14:27:18 user usb_modeswitch[3486]: usb_modeswitch: switched to 1e0e:f000 on 3/5
Dec 26 14:27:19 user usb_modeswitch[3486]: usb_modeswitch: add device ID 1e0e:f000 to driver option
Dec 26 14:27:19 user usb_modeswitch[3486]: usb_modeswitch: please report the device ID to the Linux USB developers!



---

