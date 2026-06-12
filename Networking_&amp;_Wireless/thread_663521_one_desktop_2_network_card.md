---
title: "one desktop 2 network card"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by paoloh on 2008-01-10
Hi everyone,
i installed Ubuntu 7.10 on a pc with 2 network cards and assigned ip address each (192.168.1.30 and 192.168.1.31).
When i try to ping router (192.168.1.1) it won't respond.
What should i do?

Thanks in advance

---

### Post by paoloh on 2008-01-10
Do i need to route al traffic to eth0 (card connect to router) ?

---

### Post by ladjack on 2008-01-10
yes, you should. Also you have to add default route to your routing table:

sudo route add default gw xxx.xxx.xxx.xxx

---

### Post by paoloh on 2008-01-10
i'm remote working on the Ubuntu pc via Putty but after i set route add default gw i can't connect to it.
Any suggestion?

---

### Post by ladjack on 2008-01-10
ping it.

machine you sitting at, and ubuntu host, are they in the same network?

---

### Post by paoloh on 2008-01-10
first of all thanks for helping me.

No two pcs are in different place in the town, i'm connecting via internet or, better, i was connected now i can't log into Ubuntu pc after set default gateway

---

### Post by ladjack on 2008-01-10
i'am so sorry, but i think you have to physicaly fix your routing table on ubuntu host...:(
th thing is, when you add default route, you can made mistake, but any way now ubuntu host can accept requests from network, but cannot answer it. btw, is ubuntu host router/gate?

---

### Post by paoloh on 2008-01-10
well, after restarting host i can log into again so i don't have to move physically :)

Here what i got with route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *                  255.255.255.0   U      0         0        0 eth1
192.168.1.0     *                  255.255.255.0   U      0         0        0 eth0
link-local            *                  255.255.0.0       U      1000   0        0 eth1
default         192.168.1.1         0.0.0.0           UG    100     0        0 eth0

my mistake is setting default route to router ip and not to eth0

---

### Post by paoloh on 2008-01-10
UbuntU should be a firewall/vpn between LAN <-> INTERNET

---

