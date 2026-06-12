---
title: "windows filesharing mystery"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by rogier.de.groot on 2007-05-17
Hello everybody. I've got the following setup:
client  --> router --> lan --> internet
My switch ran out of ports, and I just needed to hook up one more client, so instead of buying an extra hub, I hooked it up to a server machine that's always on anyway, via cross cable. Now all the machines in the lan are in the 192.168.5.x range - and I wanted that client in that range too, so they'd all play nice together.
To do that, I put the link between the client and router on IP addresses 192.168.6.2 and 192.168.6.1, and configured the router with two iptables lines:
iptables -t nat -A POSTROUTING -s 192.168.6.2 -j SNAT --to-source 192.168.5.7
iptables -t nat -A PREROUTING -d 192.168.5.7 -j DNAT --to-destination 192.168.6.2
and I configured a virtual interface (eth0:1) with IP address 192.168.5.7 on the router so I'd respond to ARP and such.
This basically works; the client has internet and can access the other machines on the network. The problem is, I can't use WINS names for the machines; for instance it'll connect if I type in \\192.168.5.2 but not if I use \\Hades (which is the same machine). The client also doesn't show up in Windows' network neighbourhood. It's not really that annoying - but I can't figure out what's causing this behaviour - and that annoys me a great deal - so if anyone can spot what I'm missing, please tell me.
P.S. Is there another way of doing this? It's not that weird is it?

---

### Post by rogier.de.groot on 2007-05-23
In case anybody ever has something similar: I replaced the whole routing/iptabling mess with simple ethernet bridging (now why didn't I think of that sooner). And all is now well, so if you try something like this, apt-get install bridge-utils and google for instructions...

---

