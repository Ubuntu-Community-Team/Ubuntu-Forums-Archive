---
title: "ndiswrapper: no wlan0 interface"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by carteris21 on 2006-09-15
Hi, 
   I installed ndiswrapper; then installed wireless drivers; it seems that was everything ok, but then i type iwconfig there are no wlan0. Any ideas?

---

### Post by spd106 on 2006-09-15
Has the ndiswrapper module been loaded? It should show up with **lsmod | grep ndiswrapper**. If not try **sudo modprobe ndiswrapper** again. It should give you an error message if it doesn't work.

---

### Post by anansi on 2006-09-15
im in the same boat as carteris21, so continuing the thread...

lsmod |grep ndiswrapper as root shows:

root@anansi:/home/julz# lsmod |grep ndis
ndiswrapper           177364  0
usbcore               130692  5 ndiswrapper,usb_storage,ehci_hcd,ohci_hcd

well yeah, it looked something like that, the txt file i pasted from had a bit of a ubuntu/windows conversion crisis

but still, the command 
etc/init.d/networking restart
displays the following

Reconfiguring network interfaces... Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

repeating myself (and carteris21) iwconfig does not show wlan0

---

### Post by carteris21 on 2006-09-15
yes i loaded that module, but ... I don't think that i'm able wireless on linux, because i have tryed madwifi, also on Suse ndiswrapper, and it seemed that configured good, but than iwlist scanning show no results.

---

### Post by spd106 on 2006-09-16
Could you have a look at the output given by **dmesg**. When ndiswrapper is loaded it should say what version etc. and then the name of the interface created should follow in the next few lines.

It maybe that the interface has been named differently ie. eth1 instead of wlan0.

If this doesn't work then maybe try another driver. Have a look on the ndiswrapper website for compatiblity.

---

