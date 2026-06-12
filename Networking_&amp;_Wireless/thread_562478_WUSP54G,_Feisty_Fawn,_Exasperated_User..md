---
title: "WUSP54G, Feisty Fawn, Exasperated User."
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by Logarithymic on 2007-09-28
I've done a forum search and read through countless solutions to have the WUSB54G v4 work with Feisty, but to no avail I cannot get it to work on my machine.  If anyone can offer some assistance it would be great!

---

### Post by Vadi on 2007-09-28
Does your card look like this? ([http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1129067566905](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1129067566905))

By the way you said usp in your thread title... should be usb, eh.

---

### Post by Logarithymic on 2007-09-28
I meant usb.

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper")

is my card

---

### Post by Vadi on 2007-09-28
Did you try installing the driver using ndiswrapper? Or is that where you need help?

---

### Post by Logarithymic on 2007-09-29
Yeah that's where I need help.  I blacklisted rt2570, and from there what should I do?

---

### Post by Vadi on 2007-09-29
Get it working yourself, heh. Send an email to Linksys that you're one unhappy customer!

Anyhow. I can't download the driver, I don't know the model number - so see if you can download it (make sure to select the right version, 4). In the file that you downloaded, see if there are any .inf files - if they are, please list them. We'll go from there.

---

### Post by Vadi on 2007-09-29
I'll just copy this whole lot of instructions from the ndiswrapper site, we'll be sorting through them 'till one works. At least we got a lot of options :D.

   1.
      Card: Linksys WUSB54Gv4, 802.11b/g, USB 2.0

    *
      Chipset: RT2500USB (RT2571F) (They just changed the chip and didn&#8217;t tell anybody. Be careful which version (v1/v2/v4) you buy!)
    *
      usbid: 13b1:000d
    *
      Driver 00: Ralink Driver, Open Source: [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) - 2005-07-25 / Good alternative to ralinktech.com&#8217;s driver. Works WELL.
    *
      Driver 0: Ralink driver: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) - 2005-03-25 / Drv2.0.1.0, rt2500usb.inf & rt2500usb.sys Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): works on both USB2.0 (load with modprobe ehci-hcd log2_irq_thresh=4 to avoid &#8220;usb X-Y: reset high speed USB device using ehci_hcd and address Z&#8221;) and USB1.1 (UHCI (OHCI not tested (yet?))). WEP works with 64bit and 128bit keys. but bitrate is only 11Mbit/s Note: rename the configuration file for the adapter once you installed the drivers (getting them extracted is quite a mess (WINE/Cedega) you need rt2500usb.*). &#8216;mv /etc/ndiswrapper/rt2500usb/148F\:2570.0.conf /etc/ndiswrapper/rt2500usb/13b1\:000d.0.conf&#8217; should do the trick.
    *
      Driver 1: Linksys Windows XP driver: [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp) Notes: ndiswrapper v1.1, kernel 2.6.11.7 vanilla: kernel-oops! ndiswrapper v1.2-rc1 loads fine (EHCI loaded with modprobe ehci-hcd log2_irq_thresh=4) but oopses when unloading the module and the adapter is still plugged in (Kernel 2.6.11.7 vanilla). Yet transmission seems to fail completely (except increasing &#8216;Tx Invalid misc&#8217; values nothing happens).
    *
      Driver 2: older Linksys Windows XP driver: [ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe](ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe) Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): seems to work, but only 11Mbit/s and without any encryption. no need to unplug the device before removing the ndiswrapper module. works on USB2.0, USB1.1 not tested (yet).
    *
      Driver 3:There is a native driver for rt2x00 but it has no USB support yet. View its status at rt2x00.serialmonkey.com

---

