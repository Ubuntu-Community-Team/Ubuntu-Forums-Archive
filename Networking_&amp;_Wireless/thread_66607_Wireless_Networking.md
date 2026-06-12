---
title: "Wireless Networking"
date: 2005-09-17
forum: Networking &amp; Wireless
---

### Post by HomelessJess on 2005-09-17
I have the Linksys WUSB54G V4.0 adapter ([here](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper)) and I need to know how in the hell am I supposed to get it to work with Ubuntu. I tried simply plugging it in and nothing. The CD that came with it doesn't do shit. Now what?

---

### Post by drummer on 2005-09-17
From [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
> Card: Linksys #[WUSB54Gv4], 802.11b/g, USB 2.0 -- [link here|List#WUSB54Gv4]

    * Chipset: RT2500USB (RT2571F) (They just changed the chip and didn't tell anybody. Be careful which version (v1/v2/v4) you buy!)
    * usbid: 13b1:000d
    * Driver 00: Ralink Driver, Open Source: [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) - 2005-07-25 / Good alternative to ralinktech.com's driver. Works WELL.
    * Driver 0: Ralink driver: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) - 2005-03-25 / Drv2.0.1.0, rt2500usb.inf & rt2500usb.sys Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): works on both USB2.0 (load with modprobe ehci-hcd log2_irq_thresh=4 to avoid "usb X-Y: reset high speed USB device using ehci_hcd and address Z") and USB1.1 (UHCI (OHCI not tested (yet?))). WEP works with 64bit and 128bit keys. but bitrate is only 11Mbit/s Note: rename the configuration file for the adapter once you installed the drivers (getting them extracted is quite a mess (WINE/Cedega) you need rt2500usb.*). 'mv /etc/ndiswrapper/rt2500usb/148F\:2570.0.conf /etc/ndiswrapper/rt2500usb/13b1\:000d.0.conf' should do the trick.
    * Driver 1: Linksys Windows XP driver: [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp) Notes: ndiswrapper v1.1, kernel 2.6.11.7 vanilla: kernel-oops! ndiswrapper v1.2-rc1 loads fine (EHCI loaded with modprobe ehci-hcd log2_irq_thresh=4) but oopses when unloading the module and the adapter is still plugged in (Kernel 2.6.11.7 vanilla). Yet transmission seems to fail completely (except increasing 'Tx Invalid misc' values nothing happens).
    * Driver 2: older Linksys Windows XP driver: [ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe](ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe) Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): seems to work, but only 11Mbit/s and without any encryption. no need to unplug the device before removing the ndiswrapper module. works on USB2.0, USB1.1 not tested (yet).
    * Driver 3:There is a native driver for rt2x00 but it has no USB support yet. View its status at rt2x00.serialmonkey.com Ndiswrapper may work for you, but it looks like this device isn't well supported (problems getting it to run at speeds >11mbps) If you just bought this device, it might be a good idea to exchange it for something more compatable/easier to set up.

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)  <-- some cards & their success under Ubuntu (cards with the Atheros or Prism chipsets should work best)
[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)  <-- probably try this first
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)  <-- or this if nothing else works

---

