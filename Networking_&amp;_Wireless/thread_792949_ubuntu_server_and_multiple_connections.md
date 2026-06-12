---
title: "ubuntu server and multiple connections"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by jbaileypro on 2008-05-13
Hey,

I know my way around ubuntu server now but need some help. The server has two ethernet connections, one gigabit and one 100 connections.

The server has it's own dedicated connection to the internet. The connection to the internet is through the 100mbits ethernet and the gigabit goes to the house switcher. The problem is that I need to configure the server to ONLY use its own internet connection, but then have ONLY a local connection to the house on the other adaptor.

Diagram

                 eth0&#8594;internet connection
SERVER&#8594;
                 eth1&#8594;local only connection

How do I configure this??

Thanx JJ

---

### Post by lemming465 on 2008-05-20
If you want to talk to two different networks without forwarding packets between them, just configure the two interfaces and make sure IP forwarding is off (e.g. /proc/sys/net/ipv4/conf/all/forwarding = 0).

If you need more complicated behaviors, iptables can give very detailed control over where packets are allowed to go.

I'm not sure if this helps answer your question.

---

### Post by jbaileypro on 2008-05-20
Yer that does the trick! Everything sorted now!!!

Thanxs for the help,
JJ

---

