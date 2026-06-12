---
title: "Networking with manual IP problem"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by RoofRabbit on 2014-09-07
Hi, I'm running Kubuntu 4.04.1 as an internet/file server on my home lan.
Cable modem: eth1 DHCP
Lan Connection: eth0 (current IP is 10.42.0.1)

I have Samba shares working fine both ways (server <--> pcs) and internet sharing only working on a single pc at the moment. I had to use the sharing option in network config instead of manual IP as I wanted as it was the only way to get internet sharing to work BUT linux determines the static ip (above) and my system requires the ip range to be in the standard 192.168.0.x range.

My question, how do I change (or edit) the current static ip on the linux box to the ip I need without losing the internet sharing?

---

### Post by weatherman2 on 2014-09-07
Is there some reason you don't have a router?  It would make your life much easier.

---

### Post by RoofRabbit on 2014-09-07
I'm using the linux box for my router. I just need to be able to control what my server's lan ip is, everything else is working great, I just can't use the 10.x.x.x range on my lan.

---

