---
title: "Shorewall interfaces"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by ryanfx on 2008-05-18
Hey everyone,

I had a quick question about using Shorewall as a gateway for my LAN.

I have verizon fios as my ISP and I have my topology setup as:


Internet --->  Fios Modem --->  ShorewallGatewayBox ---> Switch ---> Comps

Many guides I'm reading deal with the external NIC on the firewall being your "real" IP assigned from the ISP rather than a private address (192.168, etc).  

How should I go about setting up this small network?  Two subnets of private IP's?

Ex. a 192.168.0.x from the modem to the external NIC and a 192.168.1.x from the internal NIC to the comps?  Or is there a way to assign the external NIC my ISP IP and still play nice with the modem?

Thank you,

Ryan

---

### Post by ryanfx on 2008-05-19
bump?

---

