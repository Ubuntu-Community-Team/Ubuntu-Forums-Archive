---
title: "Can ping and browse Samba shares, but no other network services"
date: 2017-08-07
forum: Networking &amp; Wireless
---

### Post by slingy on 2017-08-07
I'm having some trouble with Ubuntu Server. It was working fine up until yesterday (and the issues may coincide with a power blackout, but that doesn't really make sense).

I can ping the server fine, it boots up ok and if I plug in a monitor and keyboard it looks fine and I can use the terminal.
I can browse shared files from my windows PC and phone, but it's a bit flakey and loses connection from time to time

But I've lost the ability to use putty, and access the Transmission WebGUI and PLEX media server via browser.
I've managed to connect to the Transmission webgui a couple of times briefly, but it drops out almost immediately.

So it's an intermittent problem, but mostly not working. It's not dropping any pings, but about 1/10 takes longer than it should.

All I've really tried is changing router port and checking my network config and restarting some services (and the server itself). Not sure what to do next.

---

### Post by slingy on 2017-08-07
Solved by disabling ipv6 as per these instructions.
[https://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04](https://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04)

I don't understand why that worked

---

