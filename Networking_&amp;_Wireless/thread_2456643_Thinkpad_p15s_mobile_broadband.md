---
title: "Thinkpad p15s mobile broadband"
date: 2021-01-16
forum: Networking &amp; Wireless
---

### Post by beknikci on 2021-01-16
I have a Thinkpad P15s [COLOR=#000000][FONT=LatoMedium]with included mobile broadband. ([/FONT][/COLOR]Integrated Mobile Broadband 4G LTE-A, Fibocom L860-GL). 
Modemmanager is installed. Ubuntu 20.04.1 with kernel 5.8.0-38-generic.
The system don't recognises that there is a modem.

mmcli -L
No modems were found


Also in the menu settings there is no option to activate mobile broadband.

lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 06cb:00bd Synaptics, Inc. 
Bus 001 Device 003: ID 04f2:b6d0 Chicony Electronics Co., Ltd Integrated Camera
Bus 001 Device 005: ID 8087:0026 Intel Corp. 
Bus 001 Device 002: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can anyone help. Thanks

---

### Post by simon-webb on 2021-01-21
Unfortunately the news on the Lenovo forums doesn't look good: according to posts on those forums, there simply isn't a Linux driver for the Fibocom L860-GL chipset yet...which means you can't (yet) use that hardware with Linux (and a lack of hardware drivers in the kernel is really a show-stopper, in the sense that there's nothing you can do about it until the driver is there). With luck it won't be long before a new version of the Linux kernel supports your hardware...meanwhile, all I can suggest is that you either live without it for now (sticking to WiFi for normal usage and perhaps dual-booting into Windows if you absolutely need to use the mobile broadband), or look into USB dongles (plug-in mobile broadband gadgets...obviously checking carefully to ensure that the chipset it uses has Linux driver support, before buying one: ideally buy from somewhere that will let you return it for a refund if it doesn't work).

---

