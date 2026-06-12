---
title: "wlan0 vs hplip"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by chazwr on 2007-11-24
I use a D-link DWL-650 Plus wireless pcmcia card (on a Dell Inspiron 8200) that has worked without issue until I installed hplip 2.7.6. (2.7.7 does not work after several attempts) With hplip installed the wlan0 stops working For No Apparent Reason. ifconfig show wlan0 but ip, netmask, etc are not set. Restarting network services solves the problem for a period of time (ifconfig show the proper settings)  but then stop FNAR again. Uninstalling hplip resolves the problem. 

Excluding various IRQs in pcmcia/config.ops has no effect. lspci reveals the card as:

03:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

proc/interrupts shows: 

 11:     863756    XT-PIC-XT        uhci_hcd:usb1, uhci_hcd:usb2, ohci1394, eth0, yenta, yenta, wlan0, radeon@pci:0000:01:00.0

Thank you for any suggestions. It would be nice to be able to print and have network connectivity.

---

