---
title: "cdc_acm module support for Verizon Novatel U727 EVDO usb modem??"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by cmorledge on 2007-11-14
I am having trouble getting the cdc-acm module to recognize a Verizon Novatel U727 (USB 727 EVDO modem) with Feisty Fawn.

I tried to follow Ken Kinder's receipe for getting these type of usb modems to work:

[http://kenkinder.com/evdo-pc5740/](http://kenkinder.com/evdo-pc5740/) 

Unfortunately, when I insert the device, I am not able to see a /dev/ttyACM0.

I am using a Lenovo T21 ThinkPad with Fiesty Fawn, though I have tried this also with Gutsy Gibbon, but it looks like Gutsy Gibbon has done something different with /proc/bus/usb/devices.

If I boot Ubuntu with the U727 inserted, dmesg shows me this:

[ 41.115183] usb-storage: device scan complete 
[ 41.118186] scsi 0:0:0:0: Direct-Access Novatel MMC Storage 2.31 PQ: 0 ANSI: 2 
[ 41.148642] sd 0:0:0:0: Attached scsi removable disk sda 
[ 41.170246] sd 0:0:0:0: Attached scsi generic sg0 type 0 

 A glance at /proc/bus/usb/devices shows me that the device shows me that the device is being picked up via USB:

P: Vendor=1410 ProdID=4100 Rev= 0.00 
S: Manufacturer=Novatel Wireless Inc. 
S: Product=Novatel Wireless CDMA 

Because the vendor and product IDs are not in ubuntu kernels (yet), I had to manually reload the usbserial module to try to get it to work with this:

rmmod usbserial 
modprobe usbserial vendor=0x1410 product=0x4100 

But when I try to unplug and replug the modem back in, /var/log/messages tells me that there is no love with cdc_acm to get it to make /dev/ttyACM0:

Nov 13 11:44:41 ubuntu kernel: [58085.976000] usb 1-1: new full speed USB device using uhci_hcd and address 7 
Nov 13 11:44:41 ubuntu kernel: [58086.144000] usb 1-1: configuration #1 chosen from 1 choice 
Nov 13 11:44:41 ubuntu kernel: [58086.148000] usbserial_generic 1-1:1.0: generic converter detected 
Nov 13 11:44:41 ubuntu kernel: [58086.148000] usb 1-1: generic converter now attached to ttyUSB0 
Nov 13 11:44:41 ubuntu kernel: [58086.148000] usbserial_generic 1-1:1.1: generic converter detected 
Nov 13 11:44:41 ubuntu kernel: [58086.152000] usb 1-1: generic converter now attached to ttyUSB1 
Nov 13 11:44:41 ubuntu kernel: [58086.152000] usbserial_generic 1-1:1.2: generic converter detected 
Nov 13 11:44:41 ubuntu kernel: [58086.152000] usb 1-1: generic converter now attached to ttyUSB2 
Nov 13 11:44:41 ubuntu kernel: [58086.156000] usbserial_generic 1-1:1.3: generic converter detected 
Nov 13 11:44:41 ubuntu kernel: [58086.156000] usb 1-1: generic converter now attached to ttyUSB3 
Nov 13 11:44:41 ubuntu kernel: [58086.172000] scsi5 : SCSI emulation for USB Mass Storage devices 
Nov 13 11:44:46 ubuntu kernel: [58091.176000] scsi 5:0:0:0: Direct-Access Novatel MMC Storage 2.31 PQ: 0 ANSI: 2 
Nov 13 11:44:46 ubuntu kernel: [58091.184000] sd 5:0:0:0: Attached scsi removable disk sda 
Nov 13 11:44:46 ubuntu kernel: [58091.184000] sd 5:0:0:0: Attached scsi generic sg0 type 0 


I try running pppd selecting USB0, USB1, USB2, or USB3, to see if perhaps the modem uses something different than what I expect, but still nothing works.    

Manually creating /dev/ttyACM0 with this does not work either:

mknod /dev/ttyACM0 c 166 0 

It is as though the cdc_acm module does not know how to handle the device.  Unloading and reloading the cdc_acm module makes no difference.

Does anyone have any clue as to how to get the proper /dev to work with this device?

Thanks.

Clarke Morledge

---

