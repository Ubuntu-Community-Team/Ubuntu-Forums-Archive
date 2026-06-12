---
title: "Masquerading using multiple external addresses?"
date: 2015-04-14
forum: Networking &amp; Wireless
---

### Post by fizgig on 2015-04-14
(Using headless ubuntu server 14.04.2)

I'm using the tutorial [here]("https://help.ubuntu.com/12.04/serverguide/firewall.html") to set up masquerading.  Works like a charm.  There's one line in the setup that looks like this:

> -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

What I'm doing is a little more involved since my server has four network ports in it.  Each network port is for a different family in our neighborhood (we're the only ones that can get internet access since we're on a hill).  Anyhow, the first port is 192.168.5.*, the second is 6.*, etc...  I've already set up a DHCP server to assign ip addresses accordingly by port.  I've also setup masquerading by duplicating the line above like so:

> -A POSTROUTING -s 192.168.5.0/24 -o eth0 -j MASQUERADE
-A POSTROUTING -s 192.168.6.0/24 -o eth0 -j MASQUERADE
-A POSTROUTING -s 192.168.7.0/24 -o eth0 -j MASQUERADE
-A POSTROUTING -s 192.168.8.0/24 -o eth0 -j MASQUERADE


Again, this all works fine.  The last piece of the puzzle is that I have four routable (public) ip addresses.  I want to assign all four to eth0 and then somehow have the rules above reflect that the first port masquerades to the first of the four public IP addresses.  The second port masquerades to the second public IP and so on.  I don't see how to do that with the above command as it just aims everything at eth0.

Anyone know how to do this?

---

### Post by Doug S on 2015-04-14
Instead of:```
-A POSTROUTING -s 192.168.5.0/24 -o eth0 -j MASQUERADE
```try this:```
-A POSTROUTING -s 192.168.5.0/24 -o eth0 -j SNAT --to external_ip_number_1
``` and so on, for the others.

---

### Post by fizgig on 2015-04-14
Thanks! I'll try that out and report back.

Edit:  Worked perfectly!  Thank you very much.  Now I'm off to figure out what I need to do to make this internet-facing server safe.

---

