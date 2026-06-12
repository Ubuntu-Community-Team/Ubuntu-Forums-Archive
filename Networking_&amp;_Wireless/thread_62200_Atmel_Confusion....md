---
title: "Atmel Confusion..."
date: 2005-09-03
forum: Networking &amp; Wireless
---

### Post by Ramza500 on 2005-09-03
Hello, I've been using Ubuntu for half a year now and just now needed wireless networking.

I've read extensively on Atmel based cards.  I have a Robanton UNC-0102W card.  I look this up on linux-wlan.org and I see that it uses the Atmel chipset.  However, lsusb lists this as a "Bus 003 Device 002: ID 069a:0321 Askey Computer Corp. Dynalink WLL013 / Compex WLU11A 802.11b Adapter".  I've installed all the atmel-firmware, atmelwlandriver-source, and atmelwlandriver-tools.  I run lvnet and nothing happens...I don't know what this means.

I read the manual for lvnet and it said that:

DESCRIPTION
       lvnet is the monitor utility for the ATMEL Wireless Card adapters. When
       the pcmcia module fastvnet_cs, the pci module  pcifvnet.o  or  the  usb
       module  vnetusba.o  is  loaded  the  lvnet  application can monitor the
       device's statistics or change it's runtime parameters.

NOTE
       In order for the application to run the driver  has  to  complete  it's
       initialization.  If  the  device's  initialization  isn't  finished the
       application won't start.


So, I'm wondering why the card is being detected however isn't initializing.

Someone please help, I've read the wiki's and tried both the berliOS and sourceforge drivers however have errors when I make both of them.  But then I read the bug reports and these drivers should be standard in Hoary, so I don't see why this isn't working.

dmesg | grep usb yields:

usbcore: registered new driver usbfs
usbcore: registered new driver hub
usb 1-2: new low speed USB device using uhci_hcd and address 2
usb 1-2: unable to read config index 0 descriptor/all
usb 1-2: can't read configurations, error -71
usb 2-1: new full speed USB device using uhci_hcd and address 2
usb 2-2: new low speed USB device using uhci_hcd and address 3
usbcore: registered new driver usb-storage
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usb 1-2: new low speed USB device using uhci_hcd and address 4
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Razer Razer Diamondback Optical Mouse] on usb-0000:00:10.1-2
hiddev96: USB HID v1.00 Device [        UPS] on usb-0000:00:10.0-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 3-2: new full speed USB device using uhci_hcd and address 2
usb-storage: device scan complete
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

Thanks for any help you can provide, I'm really beating my head on this one.

---

### Post by 0vermind on 2005-09-03
Well, it's probably a little too late now to switch but I would suggest somthing different such as Linksys Wireless-G PCI Card or Linksys Wireless-G USB Network Adapter the USB is easyer then a card (though I hav'nt tried the Wireless-G).

You may want to consider the possiblity of switching. Then, switch your gateway to somthing like a Wireless-G Cable Gateway or somthing from Linksys for the Cards/USB Adapters to connect to.

As for your problem if you don't want to switch I don't know what to tell you, I havn't had any expericene with Atmel. Sorry  :( 

Good luck-you'll need it  ;-),
Mike

---

### Post by Ramza500 on 2005-09-04
Hmmm...yeah it's a bit too late to try any other network adapters.  I've had this one and would rather not have to buy another one.

It's like the answers are there I'm just not connecting the dots.

---

