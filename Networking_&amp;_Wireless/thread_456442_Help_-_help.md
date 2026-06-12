---
title: "Help - help"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by Peter09 on 2007-05-27
I have been struggling with a D-Link DWL-G122  USB dongle for a week now, I have now installed the Prisma02 driver using Ndiswrapper. I can see the driver is installed using ndiswrapper -l.

When booting the machine the device light turns on and then off. When I look at iwconfig I only see the lo interface. What do I need to do to associate the Prisma02 driver with an interface?

Peter09

---

### Post by megabyte405 on 2007-05-27
You are probably using the wrong driver.  the DWL-122 (notice no G) is a Prism2 device, the G122 is a RT2570 (RT2500usb) device in at least the B revision.  Look on D-Link's web site to see what chipset your revision uses - if it is the RT2570 chipset (B1) then the driver is built in but a little buggy - use the device rausb0.

---

### Post by Peter09 on 2007-05-28
Thanks, you were right, I have version C of the device. I have now installed what I think to be the correct driver and ndiswrapper -l is showing a driver called netrtusb. However there still is no connection between the driver and the device. The device is shown as unclaimed. :(

Where do I go from here........:(

PC

---

