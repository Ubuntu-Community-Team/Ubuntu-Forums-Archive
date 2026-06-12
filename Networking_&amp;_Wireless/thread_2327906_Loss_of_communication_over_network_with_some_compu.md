---
title: "Loss of communication over network with some computers, not others - 14.04"
date: 2016-06-15
forum: Networking &amp; Wireless
---

### Post by nwilson5 on 2016-06-15
We have a router with two WAN ports. Some servers are upstream from our router network. I can SSH/Ping computers upstream. Upon a router reboot, I lose communication with *some* computers upstream, not others. I use DHCP with a reserved IP for my mac address. If I change my IP, I can again communicate with all the computers upstream. But keeping my reserved DHCP IP, I cannot until I reboot my system.

Explained using image below:
my computer - I can ping/ssh into computer 1 and 2. I reboot the router, and can no longer ping or ssh into computer 1 but I can ping/ssh computer 2. My computer has dhcp reservation with the router. If I change my IP using a different static IP with the router, I once again can communicate with computer 1 and 2 fully. Thing is I'd like to keep using my original dhcp reserved IP, but I cannot unless I reboot my computer. No issues communicating on the router's lan (e.g. with computer 3) after this ordeal.

[IMG]http://i.imgur.com/T1imKwh.png[/IMG]

Not sure where to go with this at the moment so any direction is appreciated. I use network-manager, restarting it does not resolve the problem.

---

