---
title: "airodump - pwr is high, but 0 data captured....why?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by and448 on 2008-07-24
Hi guys, after a lot of confusion (I've never used any flavor of Linux before) I finally got airodump-ng working.

The problem is this:

Airodump-ng has been running for about 8 hours now. PWR is on about 170, beacons is up around 200000 at the moment, and **0 #data has been captured**.

My set up is this:
wireless chipset: **centrino a/b/g**
driver: **iwl3945**
wireless card is in monitor mode under **interface ****mon0**

I've set my interface to focus on the Channel of the station I'm monitoring (11), and I'm running Airodump to focus only on Channel 11.

Also, I'm not getting anything on the bottom section of Airodump-ng output...the bit that tells you how many packets have been captured or lost.

I ran aireplay 1 to fake authentication and that worked, and I briefly got something on the bottom section of airodump-ng, saying i'd captured 8 packets, 0 lost,  but then that disappeared.

I ran aireplay 3 to get ARK (i think) and then ran aireplay 0 to force the station I'm monitoring to send an ARK (I think the acronym and terminnology I'm using might be wrong but you get the picture)

no matter what i do, 0 data, and the line telling my how many packets captured doesn't display anything at all.

The station I'm monitoring, and trying to inject into has WEP, WEP as encryption details.

What am I doing wrong?

any help greatly appreciated, cheers!

---

### Post by shortridge11 on 2008-08-03
i have the same problem, run the injection test

[http://www.aircrack-ng.org/doku.php?id=injection_test&DokuWiki=e2252c309028d2da4fd9b130129c044b](http://www.aircrack-ng.org/doku.php?id=injection_test&DokuWiki=e2252c309028d2da4fd9b130129c044b)

and tell me if you get anything from it

---

