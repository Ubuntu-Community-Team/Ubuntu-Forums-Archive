---
title: "Routing incoming WAN traffic to another server via OpenVPN tunnel"
date: 2017-09-11
forum: Networking &amp; Wireless
---

### Post by patrick47 on 2017-09-11
I live in a country where static IPs are prohibitively expensive on domestic connections. My solution has been to set up Ubuntu server on a small VPS in a datacentre and utilise the IP that comes with the VPS. . .What I can't figure out is how to route the incoming traffic at that VPS to my connection at home, where I have a small VoIP server. To be clear, I will point voip.example.com to the VPS public IP, and I need to then forward all that traffic over the VPN tunnel I set up to the VoIP server at home (voip.example.com updates with DDNS). The VPS is the OpenVPN client. I just can't figure this out, I'd sure appreciate some hints.

---

