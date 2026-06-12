---
title: "usb modem detected as mass storage device"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by Louis de Broglie on 2008-11-24
My usb edge modem which I use to connect to the internet from a mobile broadband operator is detected as mass storage device. I get this information from system log. The modem is shown in lsusb :

> Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04fc:2140 Sunplus Technology Co., Ltd
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

But wvdialconf does not detect it. I think stopping ubuntu from treating it as mass storage device may fix the issue. Anybody knows how to achieve this ?

I am using intrepid ibex.

---

### Post by timcredible on 2008-11-24
try using the network manager to connect to the internet - just click on the network icon in the top bar on the right side, and choose 'auto mobile broadband' connection.  works for my verizon usb card, works for my friend's verizon usb card (and his doubles as a micro-sd card reader too, when it has a microsd card, it shows up as both a flash drive and as a mobile broadband card).

---

### Post by Louis de Broglie on 2008-11-24
Hmm, I did not find "auto mobile broadband" . However, in the edit connection section, I did find mobile broadband section . I have configured a connection there too. But I don't see any option to dial. :confused:

---

