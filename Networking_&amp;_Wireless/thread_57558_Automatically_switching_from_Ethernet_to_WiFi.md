---
title: "Automatically switching from Ethernet to WiFi"
date: 2005-08-16
forum: Networking &amp; Wireless
---

### Post by ngc on 2005-08-16
I've recently installed Ubuntu on my Asus laptop, and generally it works well. However, what I can't figure out is how to get it to automatically switch from the Ethernet connection to the WiFi when the Ethernet cable is removed. At the moment, I have to manually do "sudo ifconfig eth0 down" to get Ubuntu to figure out that the wired connection is no longer present, and adjust the IP routing appropriately. Similarly, switching back after the Ethernet is connected again is also a manual process.

It's not a big problem, as I can work around it simply by using the WiFi connection all the time, but I'm curious as to how to set this up since Windows used to do it automatically.

Cheers,
Nick.

---

### Post by npaladin2000 on 2005-08-17
Do you have Network Manager and it's associated daemon installed?  Check Synaptic for it, but it should be installed by default.  Right click it and add it to the panel; it's listed in GNOME's list of  applet-thingys.  That'll do what you're asking for.

---

