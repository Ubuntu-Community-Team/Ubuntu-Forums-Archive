---
title: "Route throws an error"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by madsurfer on 2007-01-07
Hi
I have got installed Dapper Drake and I have an ether net and a wireless connection, when in the office there is a 192.168.1.x network and the router to the internet is 192.168.1.1. I use the ethernet card at work and originaly I was able to connect to the router and hence the internet with ease. When I needed to go to another office I used my wireless card and connect to a 192.168.0.x network, the router for this network is 192.168.0.2. Now to my problem, When I go to remote office where I use the wireless connection I can not get to the Internet, when I try to ping the 192.168.0.2 router I get "Destination Host Unreachable" if I do a ifconfig every thing seems ok and if I ping the wireless card I get a response to it. If I try to add a route to it as below I get SIOCADDRT : File exists

sudo route add default gw 192.168.0.2 dev eth1

I am new at linux and I don't really know how to go any further. Can any one please help?

Adrian

---

