---
title: "Setting autossh tunnels"
date: 2018-05-21
forum: Networking &amp; Wireless
---

### Post by andreyjust on 2018-05-21
**[SIZE=3]We have server with installed autossh[/SIZE]**

[COLOR=#242729][FONT=Arial]Number of tunnels approximately 20[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Today we add new tunnel, but not work.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]If change new tunnel instead previous the a new tunnel works, and previous there is no.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]For example:
[/FONT][/COLOR]
[PHP]-o GatewayPorts .........................................................

-o GatewayPorts .........................................................

-o GatewayPorts .........................................................

-o GatewayPorts=yes -i /home/user/.ssh/user -NL 192.168.0.1:80:5.6.7.8:80 user@server.com 
[/PHP]

work fine

[PHP]-o GatewayPorts=yes -i /home/user/.ssh/user -NL 192.168.0.2:80:1.2.3.4:80 user@servernew.com
not work
[/PHP][HR][/HR][COLOR=#242729][FONT=Arial]if we change line
[/FONT][/COLOR]
[PHP]
-o GatewayPorts .........................................................

-o GatewayPorts .........................................................

-o GatewayPorts .........................................................

-o GatewayPorts=yes -i /home/user/.ssh/user -NL 192.168.0.2:80:1.2.3.4:80 user@servernew.com 
work fine
-o GatewayPorts=yes -i /home/user/.ssh/user -NL 192.168.0.1:80:5.6.7.8:80 user@server.com 
[/PHP]

[COLOR=#242729][FONT=Arial]not work[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]May be exist restriction limit connection?[/FONT][/COLOR]

---

### Post by Skaperen on 2018-05-22
do you have error messages?

---

### Post by andreyjust on 2018-05-22
No

---

