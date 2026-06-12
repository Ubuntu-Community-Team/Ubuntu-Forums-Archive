---
title: "Network unreachable"
date: 2018-05-16
forum: Networking &amp; Wireless
---

### Post by dave1122 on 2018-05-16
[COLOR=#242729][FONT=Arial]I have an Ubuntu 16.04 system to which I’ve configured to have a static IP address.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This server connects to simple router.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]In order to make it a static IP I configured the /etc/network/interfaces file.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I can ping this router with 192.168.1.1[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I now have a second Ubuntu laptop which I’ve no plugged into the router however when I try to ping the server I get a ‘Network is unreachable’ error message.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]If I do ifconfig on the second laptop it only has ipv6 address and no ipv4 address[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Given that I’m quite new to this is anything I can check to help in the debugging?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2018-05-16
Does the router have DHCP over IPv4 enabled?

---

### Post by dave1122 on 2018-05-16
Yes, just doubled checked and it does.

---

### Post by The Cog on 2018-05-16
Can you post the output of these commands please? It should give us a starting point to work on.
```
ip address
sudo dhclient -v
```

---

