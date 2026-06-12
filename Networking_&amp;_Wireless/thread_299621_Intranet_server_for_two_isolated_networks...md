---
title: "Intranet server for two isolated networks.."
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by bushtor on 2006-11-14
Hi,

I have a ubuntu box where I want to run an intranet web server, the box has two nics, one at 192.168.33.10 and the other at 172.22.100.10.  No internet access is involved in this scenario, only intranet services.

This webserver (apache) should be available from both networks, however, traffic from any of these two networks should under *no circumstance* be allowed to 'leak' over to the 'opposite' network. 

I.e. workstations from both networks should be able to access the webserver's port 80 and 443, but nothing else.

How do I set up this so I'm absolutely sure that no traffic leaks between these two nics...?

Thanks a lot for some guidance here

regards

Tor

---

