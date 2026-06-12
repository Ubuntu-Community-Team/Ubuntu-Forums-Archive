---
title: "Ubuntu Server Network Troubleshooting"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by antar on 2007-07-15
I recently "inherited" an Asus tower that's being used as a (primarily) web server (running Ubuntu Server). I'm at a college, and so I'm behind a pretty restrictive firewall, plus a bunch of network authentication.

When I first got it, it worked straight-away, which was surprising, as it was configured with a static IP address that shouldn't have still been valid on my subnet.

Anyway, one day, I shut it down, and when I turn it on the next day, it won't connect to the network.

Network authentication for this machine works pretty much like this: at startup, a script called perfigoauth.sh runs, which uses curl to authenticate to our network with a username and password (the first thing I did was verify that both of those were good).

But the thing is, it doesn't look like it's the network authentication, as when I try to use w3m to resolve the page, it times out.

I tried using traceroute, but it failed at the first step.

I tried connecting another computer to the ethernet cable, and it's fine.

Plus, when I changed it over to a dynamic IP, it got one, no problem (I've tried ifdown eth1 && ifup eth1; again, the router gives it an IP address).

I have a Debian server running much the same setup that's working beautifully.

So, I'm wondering if anyone has any idea what ELSE could be the problem.

ifconfig eth1 gives me the follwing:
```
Link encap: Ethernet   HEaddr 00:0E:A6:9D:24:1D
inet addr:138.28.134.184   Bcast 138.28.134.255   Mask 255.255.255.0
inet6 addr: fe80::20:a6ff:fe9d:241d/64   Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:820 (820.0 b)  TX bytes:2381 (2.3 KiB)
Interrupt:185
```

---

### Post by antar on 2007-07-15
Okay: so it's *definitely* a problem with my DNS--the one place I am successfully able to ping and to access using w3m is the authentication server.

But /etc/resolv.conf doesn't show anything out of the ordinary (or is it? I really don't know too much about DNS):
```
nameserver 138.28.1.2
nameserver 138.28.4.12
search kenyon.edu
```

This all checks out (my other computer's resolv.conf reads the exact same thing).

Update: Furthermore, while dig @138.28.1.2 securesmart.kenyon.edu gives me results on my other computer, the request times out on this server.

---

### Post by keithweddell on 2007-07-15
I'm not too good with this stuff but could it be a routing problem rather than DNS?  Try entering "route" in a terminal and see if it has a default gateway.  After that I'm probably stuck.

Keith

---

### Post by antar on 2007-07-15
Nope. route yields

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
138.28.134.0    *               255.255.225.0   U     0      0        0 eth1
default         138.28.134.254  0.0.0.0         UG    0      0        0 eth1

```

which is exactly what the other computer displays.

---

