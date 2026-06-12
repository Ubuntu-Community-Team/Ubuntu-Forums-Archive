---
title: "Wireless Winbond W89C33 - Asking for help"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by bugs181 on 2007-02-14
Im running Ubuntu 6.10 (Edgy) - I THINK!?!
My problem is: My device is in the device manager. (System > Administration > Device Manager)
And its under the MCP51 PCI Bridge as Unknown (0x0033)
But if I click on this 'Unknown'  the vendor is 'Winbond Electronics Corp'.. So I beleive this to be my wireless card. How would I go about installing this/using this device with ubuntu..

My info:
Winbond W89C33 mPCI 802.11 Wireless LAN Adapter

It is located on a PCI Slot 3 (On Win XP).
PCI Bus: 6
Device: 9
Function: 0

Microsoft has a driver for it.
MS Driver Version: 1.3.1.1002
MS Driver Date: 2/22/2006

C:\WINDOWS\system32\DRIVERS\W33ND.SYS

If you require any other information just ask..

---

### Post by tturrisi on 2007-02-14
afaik winbond is not supported in linux nor does ndiswrapper support it.

---

### Post by foustala on 2008-01-08
Hi,

What is the usb-id or pci-id of your winbond device. (*lsusb* or *lspci*)

---

