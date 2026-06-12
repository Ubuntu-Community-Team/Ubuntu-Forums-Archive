---
title: "Work and Home networks"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by schapman on 2008-07-22
I imagine this is probably a fairly common issue so I'm hoping someone can help me out. 

I have a laptop I bring from home to work and back each day. 

Work connection == cabled with static IP and DNS
Home connection == wifi DHCP

the issue I run into, is when i go home the DNS gets overwritten from the dhcp so when I'm at work I have to modify it each time to be able to resolve domains.

I'm wondering if there is an easy way to have 2 separate DNS entries based on connection (as windows does it), or if there is a simple bash script that can detect if my LAN is plugged in and set the DNS based on that which can than just be overwritten with the DHCP client when I go home.

thanks for any help

---

