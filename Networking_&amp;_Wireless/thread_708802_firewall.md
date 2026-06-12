---
title: "firewall"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by tux-fan on 2008-02-26
Does Ubuntu 7.10 install a firewall by default?  If so, how to I turn it off or otherwise manage it?

---

### Post by jhetrick62 on 2008-02-26
Yes, it installs iptables.  I would recommend installing firestarter to manage it.  You can find it in synaptic.

Jeff

---

### Post by Crafty Kisses on 2008-02-26
> **tux-fan said:**
> Does Ubuntu 7.10 install a firewall by default?  If so, how to I turn it off or otherwise manage it?

Yep, iptables, which means Ubuntu ships with closed ports. :)

---

### Post by Giradman on 2008-02-26
As already posted, iptables is built into Ubuntu 7.10 and is setup fine for a personal computer - I downloaded 'Firestarter' but have not changed any settings - unless you're running a server and/or need to regulate inbound/outbound traffic, there is little need to use the program (apparently 'iptables' can be manipulated @ the terminal level w/ the appropriate understanding, but Firestarter is the GUI equivalent) - bottom line, if you are just using the computer for your 'personal use' then there is probably little need to worry about changing the 'iptables' firewall! :)

---

