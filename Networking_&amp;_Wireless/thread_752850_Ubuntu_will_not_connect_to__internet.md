---
title: "Ubuntu will not connect to  internet"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Royd on 2008-04-12
Hi Everyone
The problem is my Linux desktop will not go the Internet.
My 2 other Window XP desktops will go to the internet including email.
I am running ClarkConnect gateway – very few options as I only require the firewall.
The Linux desktop is Ubuntu 7.10.
I have tried to connect the Linux desktop directly to the router and this works. Then of course I change the settings to go back thru CC.

I tried pinging from the Linux desktop (192.168.201.13) and I can ping to the Lan card of CC 192.168.201.1 but i cant ping the Wan side of CC 203.97.218.109 but I can ping from the windows  IPs out to the internet.

I am running Static IPs everwhere
I have a static ISP address IP 203.97.218.109 GATEWAY 203.97.218.1 Dns 203.96.152.4,203.96.152.12.
So I set CC to have the external eth0 as IP 203.97.218.109 and gateway as 203.97.218.1. Internal IP as 192.168.201.1.
My other devices are 192.168.201.11 & 12& 13 with the windows default gateway as 203.97.218.109
On my Linux desktop I ran route -n and received Destination 192.168.201.0 , gateway 0.0.0.0., genmask 255.255.255.0, flags U, metric 0, ref 0, use 0, iface eth0.
resolv.conf is 203.96.152.4 & 203.96.152.12

Why is it not finding the gateway?

---

### Post by Iowan on 2008-04-12
It seems to have remembered when it was connected to router...
I've never dinked with routing tables, but you might try:```
 route add default gw 192.168.201.1
```

---

### Post by Royd on 2008-04-12
Thanks that did the trick.

---

