---
title: "need some networking expertise"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by greenway on 2005-10-27
the situation:

We have a small office network with around 10 workstations and we are connected to the internet true iPstar (satelite). I am working on setting up a Ubuntu based router/firewall. In this box I have two NIC's present, one connected to the internet through the iPstart box (working like a charm). The other one is connected to the LAN, now this is where the problem is; arp isn't able to find the MAC addresses for the workstations on the LAN.

Sometimes arp doesn't give any output at all for these ip's, other times it states that HWaddress is (incomplete). 

The infrastructure is working fine, I have checked the hub, the lines, link status and duplex form. Furthermore, untill yesterday, the iPstar box did all the routing on the network on the same infrastructure and everything was working fine.

Suggestions anyone?

---

### Post by greenway on 2005-10-27
Nobody?? Anybody??!!

update:

The problem seems to be somewhere between the router and the hub. When I ping to broadcast over the network, the individual workstations, find eachother's MAC addresses and are able to ping eachother. Sometimes when I ping broadcast from the server, some workstations also find the sever's MAC and then usually the server is also able to see some workstations MAC's. However as soon as the ARP cache is cleared, the addresses are gone and I am back to where I started.

Anybody out there with a more then average networking knowledge who would be able to help a poor fellow?

---

