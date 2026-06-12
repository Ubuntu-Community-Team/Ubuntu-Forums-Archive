---
title: "No network After P2V (Ubuntu server 17.04)"
date: 2018-04-13
forum: Networking &amp; Wireless
---

### Post by snir2651 on 2018-04-13
Hey,

I've moved my server for HP physical server to ESX 6.0 environment.

I have no LAN now.

Ifconfing shows only Loopback interface and Ifconfig -a shows 2 more interfaces (ens32, ens160)

When I try to do the "ifup ens160" command I get 
"/etc/network/interfaces:2: misplaced option
ifup: couldnt read intefaces file "/etc/network/interfaces"

In  "/etc/network/interfaces" I've put this confige in the attached file.


Help please!

---

### Post by TheFu on 2018-04-13
Support for 17.04 ended a few months ago.
Servers should really be LTS releases, like 16.04.

---

### Post by snir2651 on 2018-04-14
it was a problem with [COLOR=#000000]"/etc/network/interfaces" file,

i had mistype there.

please close this post[/COLOR]

---

