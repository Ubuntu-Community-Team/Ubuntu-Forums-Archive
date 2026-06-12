---
title: "&quot;Transparent&quot; firewall (non-NAT)"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by Selmer79 on 2007-05-12
I've been asked by my old computer-club if I could help them by being the net-admin on their next major LAN-party. I have told them I'll look into setting up the server for them, but I can't really be arsed to go to the LAN-party (I'm too old for that kinda thing now).

I was thinking about setting up a Feisty server for them that lets every internal PC have a valid external IP for IRC and such.

Last year they used ClarkConnect, but it has some exotic firewall-scripting that means you can have everyone with their own external IP, but then there is no firewall, or you can have a firewall, but then everyone share the gateway's external IP.

I'll draw up a schematic of what I want:
```
[CENTER]
Internet
|
IP: 4.3.2.1
Gateway
IP: 4.3.2.2
|
LAN
DHCP 4.3.2.10-126[/CENTER]
```

IPs 3-9 would be reserved for managed switches.

The result I'd like to get is that the firewall should prevent party-goers from bringing the internet-connection to it's knees with P2P, but people would still have their own external IP so that they can IRC without getting kicked off servers from too many concurrent connections.

Please be gentle, as it's the first time I set up a router like this.

---

