---
title: "Openvpn client and server failure"
date: 2017-04-03
forum: Networking &amp; Wireless
---

### Post by atux on 2017-04-03
[COLOR=#333333][FONT=&quot]Hi. I do have one pc in my home that acts as openvpn server. Also i have another pc in my office that acts as open vpn server for different machines. Home machine has the tun interfave on 172.16.0.0/24. Office pc is on 172.16.1.0/24.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I would lile to connect the home pc to keep the openvpn server and as well a client to the office machine but i failed to get connected.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Here are my steps:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]In the office machine i created a key labelled home.ovpn. in the home machine in the cli i did #openvpn --configure /path/of/home.ovpn[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]But i get a connection error.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I took this file to my debian laptop and i issued the same commands and i got connected.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Somethingn is wrong and i cannot figure what. could someone guide me please?

[/FONT][/COLOR]

---

### Post by TheFu on 2017-04-03
They need to be on different subnets.  Which you use doesn't matter, just they cannot be the same and none of the networks being traversed between them should be on either subnet.

It is basic networking and routing.

---

