---
title: "Gigabyte P35C-DS3R - No LAN, No WiFi"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by yonyz on 2008-11-22
Hi,
I've just installed Interpid on a machine (which dual boots with Vista) with that MoBo,
For some reason the NIC on that board isn't recognized after the installation. (Note: It's the first linux I'm trying to install on that machine)

After doing some diggings I found out that I should use the r8691 module, so I did a 'sudo modprobe r8691' and the module was successfully probed but still I didn't get a new NIC interface
(ifconfig -a only shows lo and pan0 which I think is the FireWire card)

Now about the second problem:
I'm also using a usb WiFi adapter called "Wistron DRUC-U3"
the device is recognized at lsusb, I installed all the ndiswrapper components I've found in synaptics and the ndisgtk tool, then I fired up the ndisgtk tool, pointed to the .inf file of the winXP driver, and the device was successfully installed as prisma02, then I click on the Configure Network button and I get a message saying: "Could not find a network configuration tool"
well, what's the name of that configuration tool?

Note: I've managed to connect to the internet and get this packages using my cellular phone which has a very limited data plan.

Thanks in Advance.

---

### Post by yonyz on 2008-11-22
bump.

---

