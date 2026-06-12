---
title: "Problems with Via Velocity and Realtek Gigabit cards"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by WillyWanker on 2008-10-05
Alrighty, just not having much luck with 8.04.1.

First I put in a Realtek gigabit PCI card and it seemed to work fine, but transfers off the linux box were fast while transfers to the linux box were horribly slow (like 500 KB/s). Lots of googling turned up many others with similar issues, but no solutions.

I then pulled out the Realtek card and put in one based on the Via Velocity chip. Ubuntu sees the card, loads the driver, but there is no communication from the card. Lights are on (both card and router), tried 2 different Via cards as well as connecting thru a switch and directly to the router using 2 different cables, nothing. Poured thru pages and pages of tests and ideas, none of which have worked.

My only conclusion is the included via-velocity driver sucks. I downloaded and tried to install the driver from Via, but it won't compile (craps out with an error 1 and error 2 -- yeah, sooo informative).

So I'm at a total loss, and open to any suggestions.

Thanks.

---

### Post by WillyWanker on 2008-10-05
Wow... don't everyone jump right in at once. Geez, not even a single day and already this question is on page 7.

And then the geeks have to wonder why linux will never be anything more than a niche product.

Anyway, the 8.10 beta fixes the slow transfers with Realtek cards. Too bad the rest of the OS doesn't work yet.

---

