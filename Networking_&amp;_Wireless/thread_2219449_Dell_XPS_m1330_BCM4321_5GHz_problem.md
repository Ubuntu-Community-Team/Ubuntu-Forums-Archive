---
title: "Dell XPS m1330 BCM4321 5GHz problem"
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by michal7 on 2014-04-24
[FONT=arial]I have problem with wl driver on Ubuntu 14.04 x64 (i have this problem on Ubuntu 13.10 too) installed on Dell XPS M1330 - wireless card Broadcom BCM4321. After installed wl driver from repository I can connect to my wireless 5GHz (Asus rt-n56u router) but I can't access internet or local net. If I connect to 2.4GHz network everything working fine. On Windows 7 x64 5GHz network working fine.[/FONT]
[FONT=arial]Do You have some solution for this problem?

Checked other distribution - Debian and Suse. On Debian Wireless 5GHz is working, on Suse not. Can someone help? [/FONT]

---

### Post by michal7 on 2014-04-28
Can someone help??...

---

### Post by Gerhard Maag on 2014-04-29
No solution, but some info:
Had the identical problem with 14.04 x64, that ASUS router, and a BCN4321 card in an old HP DV6700 laptop.  2.4 was great.  5Ghz connected with a strong signal, but no throughput.  Couldn't even ping the router - 100% dropped packets.  I tried various channels and widths and with no security but to no avail.  I thought the router was defective and returned it.  The guys at Staples connected to it at 5Ghz in few seconds with an iPad.  I know the BCM functions because I am demoing a Cisco EA6400 and a D-Link DIR-860L.  Both connect at 5Ghz and run well.  There seems to be some issue with the RT-N56U, 14.04 and the Broadcom card.
So I bought the top of the line AC1900 (RT-AC68U) and there are issues at 5Ghz as well.  Connects and works (I'm on it right now), but there is latency, sometimes high, but intermittent.  Is it an ASUS thing?

---

### Post by michal7 on 2014-04-30
I don't think that is Asus problem. Now I'm on Debian Wheezy x64 and Wireless 5GHz works great on Broadcom driver. I like Ubuntu, but I need working 5GHz. I tied to compile Broadcom driver on Ubuntu without success:(..

---

