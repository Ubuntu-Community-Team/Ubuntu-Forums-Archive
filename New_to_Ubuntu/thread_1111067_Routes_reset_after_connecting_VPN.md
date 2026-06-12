---
title: "Routes reset after connecting VPN"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by CBeTHaX on 2009-03-30
Hi everyone,
Im new to Linux and as you see I am in this section.
Now to my problem. I have managed to install all packages needed for starting a VPN connection. There was a problem with the routes so I called my ISP and they told me to write these lines in the terminal:

```

sudo route add -host 10.44.0.1 dev eth0
sudo route add default gw 10.44.0.1 dev eth0
sudo route add -host 217.79.68.4 gw 10.44.0.1 dev eth0

```

Okay everything is fine.
I can ping my DNS, Gateways and everything local.
Here is the route table:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
eos.dobrich.net 10.44.0.1       255.255.255.255 UGH   0      0        0 eth0
10.44.0.1       *               255.255.255.255 UH    0      0        0 eth0
10.44.15.0      *               255.255.255.0   U     1      0        0 eth0
default         10.44.0.1       0.0.0.0         UG    0      0        0 eth0
```

Then I start my VPN Connection (From the connection manager).
I can visit sites download what I want, but after about 15 seconds, everything blocks(I can't ping anything)

Route table:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
eos.dobrich.net 10.44.0.1       255.255.255.255 UGH   0      0        0 eth0
vpn.dobrich.net 10.44.0.1       255.255.255.255 UGH   0      0        0 eth0
10.44.0.2       10.44.0.1       255.255.255.255 UGH   0      0        0 eth0
10.44.0.1       *               255.255.255.255 UH    0      0        0 eth0
10.44.15.0      *               255.255.255.0   U     1      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
```

After about 1 minute my VPN connection disconnects and tells me that it failed.

Route table:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.44.15.0      *               255.255.255.0   U     1      0        0 eth0

```

I called my ISP and they told me to edit **/etc/network/interfaces**. I edited the file:

```
auto lo
iface lo inet loopback

up route add -host 10.44.0.1 dev eth0
up route add default gw 10.44.0.1 dev eth0
up route add -host 217.79.68.4 gw 10.44.0.1 dev eth0
```

Then restarted the network(also the machine) but the routes do not appear in the route table. Still that 10.44.15.0

I searched every site that can help me out, but I can't get to a possible solution.


EDIT: I forgot to mention that my Ubuntu version is 8.10 (Intrepid Ibex)

---

