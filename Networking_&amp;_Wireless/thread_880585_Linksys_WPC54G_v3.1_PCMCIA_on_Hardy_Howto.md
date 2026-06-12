---
title: "Linksys WPC54G v3.1 PCMCIA on Hardy Howto"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by avdheiden on 2008-08-05
I've recently tried to install a Linksys WPC54G v3.1 on my laptop, which is configured with Ubuntu 8.04 Amd64.

The card is detected in lspci, System...Hardware Drivers reports a B43 based (the v3.1 uses the bcm4318 chipset) card. Driver can be activated, b43-fwcutter is installed and correct FW is downloaded to /lib/firmware

However, after rebooting, the driver is reported only to be installed but not in use. Loading with modprobe failes (WME=-17). The same with the b43legacy.

Blacklisted the b43 module in /etc/modprobe.d/blacklist, unblocked the older bcm43xx module. Downloaded firmware with the bcm43-fwcutter script. Modprobe bcm43xx. Module is loaded and active. However, the NM-Applet shows no wireless cards and no wlanX on ifconfig/iwconfig

Tried the same steps on a x86 based notebook, same results. 

I suspect the bcm4318 chipset not to work with the kernel drivers.

Blacklisted both b43 and bcm43xx, installed ndisgtk, ndiswrapper, etc.


Loaded the NT/XP driver with ndiswrapper. Hardware reported present, driver reported to be loaded. No mapping, no lans found.
dmesg reports that while the kernel is 64 bit, 32 bit drivers are poorly supported. 

So what now ?

Downloaded and installed the expirimental Vista drivers from Linksys *USA* site. Ndiswrapper now maps to Wlan1 and wireless networks show up in nm-applet.

---

