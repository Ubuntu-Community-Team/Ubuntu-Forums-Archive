---
title: "Azureus trying to connect on ports it shouldn't use."
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by dercaS on 2007-12-15
Been noticing some strange behaviour in Azureus.
It tries to connect to 239.255.*.* on port 1900 UDP.
This is as far as i know the UPnP service. It's just strange that I've turned off
UPnP support in both Azureus (plugin) and in the combined router/xDSL modem.
So I'm kinda wondering why on earth Azureus keeps trying to use UPnP.

It also tries to connect to the same IP range on udp port 3702.
According to this wikipedia page that port is for some Windows Vista services?
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#Ports_1024_to_49151]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#Ports_1024_to_49151")
Obviously not just that.

And finally. Can someone tell me what Azurues uses port 16680 for?
Couldn't figure that one out.

These are all outgoing connections.
I'm pretty sure it's all due to Azureus. It started earlier today when I installed Azureus.

Azureus 3.0.4.0
Ubuntu 7.10
Java 1.6.0_03

Any comments or enlightenments would be most welcome. :)

---

### Post by dercaS on 2007-12-16
Hmm, nobody?

---

### Post by Newuser121 on 2008-05-25
Hi there,
        depending what type of modem you have got you can do a google serach. I own a d link wireless modem and I searched the firewall setting for my modem. I used the default limewire, Azures and utorrent firewall default settings. I hope this helps.

---

