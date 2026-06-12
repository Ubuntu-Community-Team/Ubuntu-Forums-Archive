---
title: "[SOLVED] Networkmanager doesn't survive Update"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by atomic_turtle on 2007-02-25
Hello,

I have Kubuntu Dapper installed on my machine and the Knetworkmanager has a rather annoying habit: After every update, it starts out refusing to recognize my wireless network. The last Update I did two days ago was also a kernel update. Right now, I'm using the older kernel version again. When I click "Show networks" in the Networkmanager context menu, my wireless network shows up. But a "sudo iwconfig" showed me that my network interface is no longer recognized. I have a TP-Link card with an atheros chipset. I think this one worked out-of-the-box for me, but I don't remember very clearly as I had long-lasting trouble with my wireless connection before getting this card. 
The /etc/network/interfaces looks like it did before, all the network interfaces (save lo) are preceded by ## and there are no details like ESSID and WIRELESS-KEY specified. 
Funnily, the Networkmanager doesn't even show the neighbour's unsecured network anymore - more precisely, that one also shows up in the "Show networks" submenu, but it doesn't come up in the main Networkmanager menu, so I can't connect to it.
I don't have a clue what the problem might be. Can anybody help me?
Do you think this problem might be solved with an upgrade to Edgy?
Thank you very much!
Regards,

atomic_turtle

---

