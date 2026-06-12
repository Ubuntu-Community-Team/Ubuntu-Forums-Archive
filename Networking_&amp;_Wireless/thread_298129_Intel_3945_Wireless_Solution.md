---
title: "Intel 3945 Wireless Solution"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Elusive_Cure on 2006-11-12
I was looking for days to find a suitable solution for my kubuntu edgy installation when i  bumped into a straight forward one at ubuntu forums. it works on both and with hardly any hassle. I tested it on two hp pavilion notebooks with edgy (clean install).

[http://www.ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+3945](http://www.ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+3945)

A small update...

After a bit of tinkering with my HP pavilion dv5235, the intel wireless was not working as before, on the dapper installation. What i did was to download the restricted modules with adept, copy /sbin/ipw3945d-2.6.17-10 to a temp folder, removed the restricted modules and copy back the ipw3945d-2.6.17-10 file back to the /sbin folder. After a reboot i was able to switch on/off the wifi with the built in button, and configure it through network management. you can also configure it manually with iwconfig-ifconfig, what suits you better. Knetworkmanager works fine, scans every available network, but lacks in terms of available options.

---

