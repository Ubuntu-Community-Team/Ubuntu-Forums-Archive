---
title: "Routing with 3 Interfaces"
date: 2014-07-10
forum: Networking &amp; Wireless
---

### Post by Michael_Purnell on 2014-07-10
With the update to PP, a routing issue has surfaced with my 3 interface gateway/firewall. I have eth0 bridged to my cable modem. eth1 services my office LAN with the address 192.168.0.1 and the network 192.168.0.0/24. eth2 services my DMZ with the address 172.16.0.1 and the network 172.16.0.0/24.

I've edited my /etc/network/interfaces to reflect this, based on guides I've viewed online. 

Bits at the end related to routing (commented out because it seems to break things worse):

```
#post-up ip route flush all
#post-up ip route add default dev eth0
#post-up ip route add -net 169.254.0.0 netmask 255.255.0.0 dev eth0 metric 1000
#post-up ip route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1 eth1
#post-up ip route add -net 172.16.0.0 netmask 255.255.255.0 gw 172.16.0.1 eth2
```

sudo route -n reports:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         BB GTW IP       0.0.0.0         UG    100    0        0 eth0
172.16.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
BB CONN NTWK    0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

My connections on the LAN seem to struggle with packets going out.

---

### Post by The Cog on 2014-07-10
You will need to enable packet forwarding - it' a setting in /etc/sysctl.conf, you need to uncomment a line and reboot.
You will need to enable ip masquerading on eth0 to perform address translation
Your connected hosts will need entries in their routing tables using your gateway as the next hop.

Your routing table looks fine to me, except I'm a little surprised that the internet link is a /24 (not necessarily wrong though).

If you still have problems, I would suggest using tcpdump to list the packets going in and out of each interface to work out where it's going wrong.

---

### Post by Michael_Purnell on 2014-07-10
Yes, the Internet link is a /24, which may be related to it being a business connection with static IP. Packet forwarding is on. Masquerading is on. It is only on the outbound packets that I have issues. 

<quote>[COLOR=#000000]Your connected hosts will need entries in their routing tables using your gateway as the next hop.</quote>

Do you mean by this, something beyond specifying the default gateway for the respective subnet on each host?

1. It is clearly an issue with the Gateway
2. There may be a firewall issue instead of routing

I will have some time for sleuthing this weekend, and will report.[/COLOR]

---

### Post by The Cog on 2014-07-11
I should have been more clear. Yes, if your Ubuntu machine is their default gateway then that will do fine. They just need to know to forward their internet packets to you.

It could be a firewall issue. Easiest, if you can bring yourself to do it, is to temporarily disable the firewall. But my preferred approach would be to use tcpdump to watch what's happening on each interface.

---

