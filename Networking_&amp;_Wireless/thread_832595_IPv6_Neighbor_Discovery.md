---
title: "IPv6 Neighbor Discovery"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by devils302 on 2008-06-17
I'm trying to get Neighbor Discovery working on my Ubuntu laptop, I don't know too much about working with ifconfig or *nix networking tools, but I'm a CCNA and the DSL admin for my own line, so I know about Cisco networking, but don't know any of the *nix commands.

Here's my problem:
I've got a /48 block routed to my DSL as such:

 bandwidth 3000
 ip unnumbered Loopback103
 ip helper-address 207.154.64.10
 atm route-bridged ipv6
 ipv6 address 2001:19F8:17::/48 eui-64
 ipv6 enable
 ipv6 ospf 4927 area 0
 pvc 2/592 
  vbr-nrt 3312 3312 2000
  no ilmi manage
  encapsulation aal5snap

I have enabled IPv6 on my Laptop, and am trying to get Neighbour Discovery working on my Ubuntu laptop. I've got a switch behind my modem, and I can get a dynamic IPv4 address from the ISP, but IPv6 Neighbour Discovery will not auto detect and give me a routable address.

Could someone please help me by showing what the config should look like to have this work in '/etc/network/interfaces'?

Any help would be appreciated :)

---

### Post by dmm1983 on 2008-06-18
also how do turn of ip4 so it can just pickup ip6

---

### Post by devils302 on 2008-06-18
> **dmm1983 said:**
> also how do turn of ip4 so it can just pickup ip6

IPv4 and IPv6 work simultaneously. Disabling either is not a good idea because many websites and WAN networks still only support IPv4.

What would be your reason for turning off IPv4?

---

