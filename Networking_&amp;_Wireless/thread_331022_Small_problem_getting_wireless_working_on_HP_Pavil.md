---
title: "Small problem getting wireless working on HP Pavilion zv5000 for Kubuntu Edgy"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by aerojad on 2007-01-04
Well, this whole ubuntu expierence worked so well for me on the destop I decided to convert my laptop as well.  I figured wireless would be the hardest part but after some reading, I think I got it all done correctly.  Almost.

First up, the driver needed is for the BCM4306 802.11b/g Wireless Card.  Got that downloaded.  Used ndiswrapper to install it.  It appears things installed correctly, yet it refuses to load.

Example:

> aerojad@Jeeblet-II:~/Downloads/64-bit_Broadcom_54g_Drivers$ sudo ndiswrapper -l
Installed ndis drivers:
netbc564        driver present, hardware present
aerojad@Jeeblet-II:~/Downloads/64-bit_Broadcom_54g_Drivers$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

All that I could find online were examples of that error being for an improperly installed driver, but if that was the case, wouldn't ndiswrapper -l say something different?

---

