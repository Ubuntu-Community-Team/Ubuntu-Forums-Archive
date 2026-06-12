---
title: "IWL4965 UDP problems (skype/jabber) on Hardy"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by ivotoby on 2008-09-22
Hi,

Usually I can get my answers from here without actually having to post:D, but I haven't found a solution to this yet. I have a HP8510W laptop running Hardy on 2.6.24-19-generic. 
This laptop uses the intel 4965 wireless chip which seemed to be working out-of-the-box with the IWL4965-module. Transfer speeds are ok, scanning works and I could connect to my wireless WPA2 network without any problems. However; it seems there's something going on with UDP-traffic. AFAIK Skype and Jabber both use UDP ; both do not work properly. Skype messages I sent are delivered about 3 to 5 minutes later, and connecting to a Jabber-server simply doesn't work.
I've tested Skype and Jabber on a ordinary wired connection; both work great and problems seem to be solved, but not on wireless.
I've tried changing several options when loading the iwl4965-module (hwcrypto, qos_enable etc.) and installed the backports-modules without any effect. I'm not sure if the drivers from [www.intellinuxwireless.org](www.intellinuxwireless.org) are better/newer than the ones I have running now 1.2.25 (since I can't find a version anywhere)
Has anyone encountered this and found a solution? Should I install the drivers from [www.intellinuxwireless.org](www.intellinuxwireless.org) ? 

Thanks!
Ivo

---

