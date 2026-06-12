---
title: "Sees router but not Internet"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by Volarz on 2006-07-29
Problem: Well, see title.

Setup: Ubuntu running off Virtual PC (which is on XP home).

Some attempts:
Reading other threads I'll note:

1. I can't access [www.google.com](www.google.com) from Firefox but I can ping its ip address (64.233.183.99).
2. When I run a traceroute on google's ip address I get:
Hop---------Host Name---------IP
1          192.168.131.66   192.168.131.66 
2          no               reply
3          no               reply
4          no               reply
..etc...

Thanks for any help.

---

### Post by ofimiano on 2006-07-29
I just got over the same problem. I had to buy a new ethernet card, one that was natively supported by Ubuntu. Go to [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards) and pick one from there. Worked immediately after install and reboot.

---

### Post by Volarz on 2006-07-29
Thanks ofimiano.
However, I'm using a wireless USB which connects to the router. I know the wireless USB works fine because I have no problems using right now in XP.

---

### Post by Volarz on 2006-07-30
Problem Fixed!
Had a DNS problem. A little

sudo ifdown eth0
sudo gedit /etc/resolv.conf
sudo ifup eth0

did the trick.

---

