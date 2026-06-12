---
title: "iptables and KVpnc - losing connectivity on disconnect"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by kalahari875 on 2006-11-18
Calling all iptables/VPN experts out there. :) I was trying to get pptpconfig to connect to my workplace PPTP VPN and was getting the infamous "ARP Cache" error, so I tried using KVpnc instead (Kubuntu Edgy 6.10). I ended up removing Firestarter (even though I had the user-pre commands in to pass PPTP traffic, it seemed to be blocking connectivity), and replaced Firestarter with the attached simple iptables configuration: [ATTACH]19572[/ATTACH]

I can connect fine from my workstation, and can connect to the PPTP VPN fine, but every time I disconnect from the VPN I lose networking (or at least DNS)--nothing can get out on POP, HTTP, etc. because of the failure to find the servers. Every time I disconnect I have to reload my iptables configuration via iptables-restore.

When I connect via the VPN, I add routes to the remote network via dev ppp0 on the after connect command, and I never actually delete these routes, but I didn't think I needed to once ppp0 disconnects.

What am I doing wrong? I should be able to disconnect the PPTP VPN and still have connectivity. Thanks in advance.

---

