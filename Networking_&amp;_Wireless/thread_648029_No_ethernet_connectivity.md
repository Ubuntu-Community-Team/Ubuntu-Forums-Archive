---
title: "No ethernet connectivity"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by satjat on 2007-12-23
I am trying to connect to the internet with my new ubuntu box.
The system seems to be detecting my card (realtek 8139).
I only have the onboard network card on the pc but ifconfig lists 2 adapters and the local. eth0 and etho0:avah
eth0 only has ipv6 address and avah has an ip that cannot be issued by the dhcp server on the router
when I try ifdown/ifup I get "no dhcp offers"
I cannot access anything since I can't even get an ip.
In the harware info window only one card is listed.
Is there any case that even the card seems to be detected I need an additional driver or something?

The configuration is a little complicated but it works on xp perfectly
There is a 3com wireless access point with static ip 192.168.1.3 put in client bridge mode
Then a ZyXEL router with ip 192.168.1.1 with dhcp server
The pc is set to dhcp mode. Even on static ip, with a correct address, not even the access point can be pinged
thank you all in advance

---

### Post by rkd on 2007-12-25
If you haven't solved the problem yet, this might help:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

