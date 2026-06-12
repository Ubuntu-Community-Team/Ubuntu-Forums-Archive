---
title: "Forward all SSDP from mediatomb to VPN Cpnnection"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by robert-woodward on 2014-05-11
Hi All,

I have set up an Openswan L2tp / IPSEC VPN for us to connect back to when away from the house.  This works perfectly in that we can browse the folders on the server.  The bit I am struggling with, and have now spent several days searching the internet for, is how to get the Multicast traffic from Mediatomb to be sent through to the clients connecting in.

My setup is:
eth1 (external ip)
eth0 (Internal ip)
pppX (0 - 20) are the connections created on active VPN connections.

Mediatomb interface is set to eth0, and I would like to forward the SSDP (239.255.255.250) traffic from that down each of the ppp interfaces as they connect.

Can anybody give me any steer on this please?


Thanks, Rob.

---

### Post by robert-woodward on 2014-05-12
My layout I am currently achieving is:

[B]Internal Network <===> [B]eth0 (DHCP Server 192.168.80.1 range 192.168.80.2 - 192.168.80.199) [Ubuntu Server] eth1 (DHCP Client - 94.173.XXX.XXX) <======> [B]www <=====> [B]Android Mobile (O2 UK)

[/B][/B][/B][/B]
I have since altered my xl2tpd.conf to use the following settings:
```

[global]
ipsec saref = no
listen-addr = 94.173.XXX.XXX
port = 1701




[lns default]
ip range = 192.168.81.2-192.168.81.249
local ip = 192.168.81.1
refuse chap = yes
refuse pap = yes
require authentication = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

```

moving all ppp connections to the 192.168.81.X range, instead of as they were previously, which was living on the end of the 192.168.80.X range with the rest of my home network, albeit on a different netmask.  I felt this might make my understanding easier of networking, however, I'm still drawing a blank.

I believe I need "route add ......." and / or "iptables -A FORWARD......" to get the multicast traffic moving from eth0 where mediatomb is broadcasting to ppp0, ppp1, ppp2........ as the appear.  This I think needs to go into: /etc/ppp/ip-up.d and a reverse operation to remove them in: /etc/ppp/ip-down.d however, I don't know what the rest of the route add and iptables -A FORWARD should look like, my "testing" so far saw my internal network stop completely when a VPN connection was made?!  Not particularly helpful!!!

Any help very gratefully received!

---

### Post by robert-woodward on 2014-05-16
Anyone help me out on this please?!

---

### Post by robert-woodward on 2014-10-04
Still seem to be on my own with this one?! I've recently tried smcroute to forward the IGMP through to ppp0, the interface created by the VPN with the following commands (239.255.255.250 is minidlna.  I have both that and Mediatomb running as DLNA servers):

```

smcroute -d
smcroute -j eth0 239.255.255.250
smcroute -a eth0 192.168.80.1 239.255.255.250 ppp0

```

but I get the following error with the last command:
***daemon error: Warn: invalid output interface***

Any advice would be greatly appreciated, getting really quite frustrated with it now!!

---

