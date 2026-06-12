---
title: "Cannot access to internet by vpn"
date: 2019-01-11
forum: Networking &amp; Wireless
---

### Post by miodas007 on 2019-01-11
Hi,
when i connect to vpn to my work intranet, i have access to local network, but i lost access to internet. When I ping some external site by name, it resolve ip, so i assume that dns resolving work fine. I have not idea why I can 't access to external site behind vpn. IT-ops in my work tell that they don't deny external network access in vpn config, so I assume that is a problem in my configuration.
I use network-manager-vpnc client - vpn cisco  compatibility mode (vpnc). Ubuntu 18.10

Have you some idea what i can check ?

---

### Post by The Cog on 2019-01-11
Most corporate VPN clients route all your internet traffic over the VPN, cutting off your direct internet access. This is deliberate, and is intended to ensure that your laptop/pc cannot operate as a path between the internet and the corporate vpn bypassing their corporate firewall. I know the Cisco VPN client does this. I don't know if it is configurable, but you would be opening yourself to disciplinary action if you subverted their security arrangements.

---

### Post by miodas007 on 2019-01-12
Thanks for reply. Probably I wasn't precise when i described my problem. I don't want bypass vpn and connect directly to internet. I must have access to work local network and internet being behind vpn, so it is perfectly good for me that when i want hit to some site on internet it will go via some server of my employ. I asked about it it-ops in my work, but they assume that don't cut external network on vpn, so i don't know why this is not working for me.

---

### Post by The Cog on 2019-01-13
Ah, now I understand. So IT do not mind if you still have direct access to the internet. 
I do not know how the Cisco VPN client disables direct internet access. I guess we need to figure that out.

Let's see what it does to your routing table. These two commands will show you all the routing table information:
```
ip rule list
ip route list table all
```
Can you post the output of these two commands, run both with and without the VPN running. But you might want to replace your public IP address and your employer's IP addresses with words instead, to avoid publishing sensitive information.

---

### Post by praseodym on 2019-01-13
Does your corporate network know the MAC addresses of your devices to route them outside (not only knowing them -as they do, otherwise you couldn't access that network at all)

Edit: Does the corporate server use LZO compression? If yes, you need to activate it on the client as well.

---

