---
title: "network bridging"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by source on 2006-12-22
I have my connection set up like so


                                                               Xbox 360 < ------------ PC <----------ROUTER<----dsl modem


I connect my PC to my xbox with an ethernet cable (rj-45)

I basically do not have the space to connect the router directly to my PC and must bridge from my PC to the xbox.

I downloaded firestarter, bridge-utils, and configured for hours with my network and i cant get it to work...


I am all wires and no wireless so my eth0 and eth1 are both wired. eth0 wasnt showing up for me till i assigned it as static and even then the xbox wasnt connected.

could someone please tell me the gateway subnet mask, DNS, IP address, etc i need to configure on my xbox and pc?

my Working configuration for the Xbox using ethernet direct to router was
```
IP Address 192.168.1.100 
Subnet Mask 255.255.255.0
Gateway 192.168.1.1
primary DNS server 192.168.0.1
secondary DNS server 0.0.0.0

```


My working PC configuration is
```
eth1 =address DHCP
eth 2 address DHCP
DNS server 192.168. 0.1
```

?](*,) :-k :confused:

---

### Post by source on 2006-12-22
anyoneZ?

---

