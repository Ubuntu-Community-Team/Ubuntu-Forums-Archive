---
title: "EXPERT advice on network setup with OPENVPN gateways"
date: 2014-07-20
forum: Networking &amp; Wireless
---

### Post by nicolasdiogo on 2014-07-20
Dear network experts


i would like to have a setup at my home office whereby all traffic is routed through OPENVPN

at present, i have each pc has a configured OPENVPN

i have considered purchasing a small motherboard that i could use as a router that 
connects to my broadband provider that uses **PPPoE**, and
setup 2 different OPENVPN gateways (that i can have at the same time) from my VPN provider

but i fail to understand the technicality of this setup.


could you please provide me with some guidance on how to get started?
and reading material to enable me to complete this seutp?


many thanks,

---

### Post by miguelpires on 2014-07-20
Hi,
I've a similar setup at home but I use Zentyal for this (is Ubuntu + the packages created by Zentyal). It uses OpenVPN + certificates and is easy to setup. I've 2 Gateways, 1 for PC other for mobiles.
I think is the easy way to setup this.
Regards
Miguel

---

### Post by nicolasdiogo on 2014-07-21
Thanks Miguel

I have used Zentyal for many years.

Let me clarify my idea.

I would like to have ALL my LAN traffic routed through a third part provider; such as [http://torguard.net/](http://torguard.net/)

Só i would need as i understand require a system to connect to this VPN and to work as a gateway for the LAN.
This set up of VPN client and gateway simultaneously is what I am failing to find info about.

Please let me know if I should provide further info.

Regards,

---

### Post by nicolasdiogo on 2014-07-24
[http://networkfilter.blogspot.co.uk/2014/05/defend-your-network-and-privacy-vpn.html?m=1](http://networkfilter.blogspot.co.uk/2014/05/defend-your-network-and-privacy-vpn.html?m=1)

The link above explains how a similar setup to what I am looking for can be done with BSD

So is it doable in ubuntu too?


Thanks

---

