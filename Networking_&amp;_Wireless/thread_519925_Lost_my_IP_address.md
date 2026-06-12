---
title: "Lost my IP address"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Nathan_Scott_Grey on 2007-08-07
We moved our office downstairs and then reassembled our network. I reconnected our Ubuntu server to the internet and was able to get out. I fired up my virtual machines and they can get out to the internet. Now, the virtual machines still can get out, but an `ifconfig` shows me eth0 no longer has an IP address (not even a 169.254.x.x address). 

What do I have to do to get my server to draw a new IP address (it pulls DHCP from the router that splits up the public IP addresses on the network)?

I can configure statically if I had to, but that only avoids the problem, it doesn't fix it.

I configure the interface statically. I can ping the other devices on the network, but I can't get out to the internet.Nothing stopped it before. Is there something I should be looking at?

---

