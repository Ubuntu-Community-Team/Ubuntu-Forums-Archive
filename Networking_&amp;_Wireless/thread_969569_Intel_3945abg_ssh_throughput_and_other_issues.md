---
title: "Intel 3945abg ssh throughput and other issues"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Neil_Bell on 2008-11-03
OK had this issue start in hardy but it seems to have followed into intrepid as well. My ssh transfers are terrible slow. Generally in the 700-800K range. Seeing as i do a lot of transfers to my server this way the quickest fix in hardy way to roll back my kernel from .21 to .20 where it worked fine. Throughput was around 2.5MB not great still but better then nothing. Now I have upgraded to Ibex and I'm back to 700-800K. 

I've tried the compiling the latest openssh as well as swapping from network manager to wifiradar and wicd. Now i'm onto [http://ppa.launchpad.net/network-manager/ubuntu/intrepid](http://ppa.launchpad.net/network-manager/ubuntu/intrepid) main for network manager with no results. The iwlwifi project is now part of the kernel so no need for drivers. I'm not the only one with this issue any ideas.

Edit* also went [http://linuxwireless.org/](http://linuxwireless.org/) and compiled the latest driver from the 31st Oct still can't get over 1MB.

---

