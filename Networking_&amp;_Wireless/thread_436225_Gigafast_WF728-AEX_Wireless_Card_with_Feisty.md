---
title: "Gigafast WF728-AEX Wireless Card with Feisty"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Trevor4706 on 2007-05-07
My Gigafast WF728-AEX wireless PCMIA card worked "out of the box" with Dapper.  I recently upgraded to Feisty.  Immediately after the upgrade, and until last Wednesday, my card also worked "out of the box".  It has now stopped.  Wireless networks are detected OK, but when I try to connect to the network Gnome Network Manager shows the "connecting" icon and eventually times out.  When I try the KNetworkManager the progress bar sticks at 28% "configuring the network".  I've checked my card on a Windows computer and it is functional.

Any ideas what I could have done to bring this about?

---

### Post by ridgid on 2007-09-18
I am on a debian 4. system, but was able to use my card with the live kubuntu 6.10 cd and not with my installed debian system

found I think it was under dmesg that the firmware was not loaded
had to install blob from 

[http://prism54.org/fullmac.html](http://prism54.org/fullmac.html)


» Version 1.0.4.3 (for ISL3880 and ISL3890)
and rename it to
/usr/lib/hotplug/firmware/isl3890

then i was able to start it via the control panel NP

hope this helps 
Ridgid

---

