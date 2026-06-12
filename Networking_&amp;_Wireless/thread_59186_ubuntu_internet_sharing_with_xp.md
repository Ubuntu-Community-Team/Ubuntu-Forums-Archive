---
title: "ubuntu internet sharing with xp"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by andy_satriani on 2005-08-23
hi sorry for asking a noob question,
i want to configure internet sharing on my ubuntu
computer A:
running ubuntu, have two lan cards eth0 and eth1
the eth0 is configured to connect to the internet provider using wireless lan.
eth0 settings (internet setting)= -ip address = 172.16.0.75
                          -subnet mask = 255.255.255.0
                          -gateway address = 172.16.0.1
                           - DNS = 172.16.0.1
the eth1 is configured to connect to computer B witch is using Win XP.
eth1 settings (LAN) = ip address = 192.168.0.1
                                   subnet mask = 255.255.255.0
                                    gateway = blank
i have ran MASQUERADE, i have tried firestarter, all of that wont work
can someone help me, thx alot guys  :grin:  :grin:

---

### Post by Jussi Kukkonen on 2005-08-23
Are you using the Masquerade HOWTO on Linux Documentation Project? Especially the sections on [IP Forwarding](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html)  and [Configuring NT client](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/configuring-winnt.html).

. . . just crossed my mind: did you know that if you're connecting a network card straight to another network card, you're going to need a crossover cable -- normal ethernet cable is no good?

---

### Post by andy_satriani on 2005-08-27
thx jussi, i have done it ^^

---

