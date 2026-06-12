---
title: "Starting hotplug subsystem ... freeze after deinstalling ndiswrapper"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by licorna on 2005-11-26
I have this problem with my laptop. I installed ndiswrapper and the drivers for Realtek wireless cardbus (info below). It didn't work very well so i tried installing some other driver. When i deinstalled the first driver, restarted the laptop and when starting again it freezes in * Starting hotplug subsystem ... and nothing happens (no, CTRL+C doesn't work).

I had to use one of the live cd's that came with my ubuntu shipment, mount my hard drive and remove the file /etc/modprobe.d/ndiswrapper.

I have no idea why the system freezes trying to start the hotplug. I tried with the card plugged and unplugged, with none usb plugged in but nothing worked for me.

The card chipset is:  Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
Laptop model: hp ze1250

So, this is not a Why-do-i-solve-a-problem? post, it is a I-did-solve-it-this-way, but if anyone has any information about it would be good to share.

Rodrigo

---

