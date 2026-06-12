---
title: "Wireless Broadcom installed but not able to connect"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by onlybui on 2007-02-21
Ok I think I have it installed correctly but for some reason it doesn't work or does not connect to my access point. 
I've  lspci -v and gives me this
0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1363
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at b8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
I installed gnome-network to configure the wireless newtwork drivers using ndiswrapper, I downloaded the correct driver from hp site by the way I have a dv9000t and the inf is installed which is bcmwl5.

I've sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

But when I do this, I get this sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

So does that mean its not installed correctly?

---

### Post by Edache on 2007-02-23
Try installing wlassistant, it worked on my airlink wireless usb adaptor.

---

### Post by onlybui on 2007-02-23
I followed this and it worked

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

hope this help people... by the way Im using ndiswrapper 1.28.....

---

