---
title: "How recover wifi after upgrade 12.04 -&gt; 14.04"
date: 2014-09-01
forum: Networking &amp; Wireless
---

### Post by slave2live on 2014-09-01
I have an ACER Extensa 5620Z.
After update to 12.04 I lost my Wifi function and tried all the advice on the forums. No luck.
After update to 14.04 WiFi still did not work. New problem, can not restart or shut down. Again tried all forums, reinstalled 4 times, no luck.
GOOD NEWS - Soulution: 
In terminal:
> [COLOR=#3B3B3B][FONT=Ubuntu Mono]sudo apt-get purge[/FONT][/COLOR]
[COLOR=#3B3B3B][FONT=Ubuntu Mono]sudo apt-get autoremove[/FONT][/COLOR]
[COLOR=#3B3B3B][FONT=Ubuntu Mono]sudo dpkg --configure -a[/FONT][/COLOR]
[COLOR=#3B3B3B][FONT=Ubuntu Mono]sudo apt-get remove --purge bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=#3B3B3B][FONT=Ubuntu Mono]sudo apt-get install linux-firmware-nonfree[/FONT][/COLOR]


I had then restarted foth a forced power-down button

The result - 
WIFI IS WORKING 100%.
SHUTDOWN and RESTART WORKING 100%

---

