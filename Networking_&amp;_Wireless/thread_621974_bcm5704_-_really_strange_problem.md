---
title: "bcm5704 - really strange problem"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by hozone on 2007-11-24
i'm trying to install ubuntu server 7.10 on a hp proliant dl360 g4
with a broadcom nextreme bcm5704 gigabit card NC7782

i've installed it without netword because
1) card is detected
2) card get dhcp
all works

when i try to get mirrors, it stops at 40%, so i must install without detecting mirror.

i log in to y system and here the strange problem:
* i can ping all ip inside and outside
* i can get data only FROM some ip (all internal IP of my network), and some external.
example
wget [http://www.libero.it](http://www.libero.it) [WORKS]
wget [http://www.ubuntu.org](http://www.ubuntu.org) [DO NOT WORKS]
------
--15:25:02--  [http://www.libero.it/](http://www.libero.it/)
           => `index.html.1'
Resolving [www.libero.it](www.libero.it)... 195.210.91.83
Connecting to www.libero.it|195.210.91.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [        <=>                          ] 85,124        38.78K/s

15:25:06 (38.72 KB/s) - `index.html.1' saved [85124]
---------
--15:25:35--  [http://www.ubuntu.org/](http://www.ubuntu.org/)
           => `index.html.2'
Resolving [www.ubuntu.org](www.ubuntu.org)... 147.83.195.18
Connecting to www.ubuntu.org|147.83.195.18|:80... connected.
HTTP request sent, awaiting response...
---- (here the system stalled, do not go on)

another strange thinks is that IF i start system from ubuntu 6.06 desktop install cd, the card work completely works!!!

i've noticed that tg3 on ubuntu 6.06 is 3.47
on 7.10 is 3.77

ethtool -i eth0
driver: tg3
version: 3.77
firmware-version: 5704-v3.27b
bus-info: 0000:02:02.0

i've also try debian etch and centos 5, but both has the same problem same problem.

i've try combination of
ethtool -s eth0 speed 10 duplex halt autoneg on
speed 100
speed 1000
duplex half or full
autoneg on off
NONE works

i've try upgrading to 3.71 or 3.81 tg3 driver from broadcom site, but none works...

only ubuntu 6.06 desktop seems to works, now i'm downloading 7.10 desktop, and 6.06 server to try if one works.

i CAN't change net card, cause dl360 has not pci port available.

ANY suggestion will be apriciated!


regards,
Davide

---

