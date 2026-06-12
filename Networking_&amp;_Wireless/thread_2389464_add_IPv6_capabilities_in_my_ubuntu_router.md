---
title: "add IPv6 capabilities in my ubuntu router"
date: 2018-04-17
forum: Networking &amp; Wireless
---

### Post by atux on 2018-04-17
For lab purposes i have an ubuntu server 12.04 and it acts as router. It is server edition 32bit and runs headless. It has 3 ethernet cards (eth0, 1, 2). 
[LIST]
[*]eth0(192.168.0.1/24): is used for WAN cannection and connects to another router.
[*]eth1(192.168.1.1/24): is used to connect the LAN to the router. All traffic from this ports gets Internet(NAT) to eth0. It has dhcp service enabled on that interface
[*]eth2(192.168.2.1/24): is used to connect the LAN to the router. All traffic from this ports gets Internet(NAT) to eth0. No DHCP on that interface
[*]eth1 & eth2 cannot see each other
[/LIST]
For DHCP i am using dnsmasq and it works really fine. Here is my config:
```
interface=eth1
dhcp-range=192.168.1.9,192.168.1.99,255.255.255.0,1m
dhcp-option=option:router,192.168.1.1
dhcp-option=option:dns-server,192.168.1.1
```

So far so good. Now, for lab purposes i need to setup this machine to act as IPv6 dhcp server on eth1,
but give Global IPv6 addresses(like an ITSP). 
How, do i enable IPv6 in this system, please? What changes does it need on dnsmasq config?

Is it possible to enable the router do all the parsing from IPv4 to IPv6? I need to have some linux PCs get 
only IPv6, but to be able to communicate with IPv4 pc in the same LAN and in the Internet.

---

### Post by Tadaen_Sylvermane on 2018-04-17
12.04 died in 2017. It is now 2018. You need to upgrade to 16.04 to get much help here on these forums. People don't support old outdated releases usually.

---

### Post by atux on 2018-04-18
Hi. just finished of a clean install of 16.04.04 LTS and i have exactly the same setup. the system is functional and i am now up to date regarding OS. i am looking for some help with the IPv6 DHCP, please.

---

