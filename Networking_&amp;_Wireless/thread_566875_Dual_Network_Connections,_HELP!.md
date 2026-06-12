---
title: "Dual Network Connections, HELP!"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by rkrizan on 2007-10-04
Okay, here's my scenario, I have 2 routers. People use both of their routers. I have 1 desktop machine which has 2 NIC cards. I am connected to each router with the 2 NIC cards, so people using either 1 router or the other can print using CUPS on that machine. That part works. I am able to connect to both networks just fine. Firefox will not work because it doesn't know which connection to use, which is fine. I disabled routing out to one of the routers with this:

route del -net 0.0.0.0 gw 192.168.2.1 dev eth0

That way it uses the other router for traffic out to the internet, yet still maintains connectivity to both routers.

Here's the problem. How do I set it up, so BOTH network connections start on bootup, and it somehow disables routing out to one of those routers (like with that command above) on boot?

Please help, thanks in advance.

---

### Post by helgman on 2007-10-04
This is how I did it on a Debian Server.

Edit /etc/network/interfaces and make it look something like this (depending on your setup):
```
auto eth0
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        gateway 192.168.1.1

auto eth1
iface eth1 inet static
        address 192.168.2.10
        netmask 255.255.255.0
```

Then restart the network and take look with route -n, there should be only one route to 0.0.0.0.

(Sorry for not explaining but I'm running out of time ...  please let me know if it doesn't work out or if you want an explanation).

Regards,
Helgman

---

### Post by rkrizan on 2007-10-04
Works perfectly, thanks.

---

