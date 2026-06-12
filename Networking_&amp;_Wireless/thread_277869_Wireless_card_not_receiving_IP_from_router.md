---
title: "Wireless card not receiving IP from router"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by fred22 on 2006-10-15
Hi,
This seems bizarre to me, esp. as it was working some time age.

I have a Netgear MA521 wireless card in a laptop running xubuntu. The wireless card can see my network if I do iwlist scanning. Then if i run iwoconfig the correct ssid and access point are listed. If I run dhclinet I never get an IP address, yet if I check my router logs the router is sending offers, but never getting an ack.
Any suggestions gratefully received.

---

### Post by fred22 on 2006-10-15
Thought I should add that if I assign a static IP address I can ping the router, but not connect to the internet.

The router is working fine with another Ubuntu box that I am writing this post on.

---

### Post by spd106 on 2006-10-15
Do you have a misconfigured firewall?

You should be able to use a static address, just make sure that you have the routers ip address as the gateway.

---

