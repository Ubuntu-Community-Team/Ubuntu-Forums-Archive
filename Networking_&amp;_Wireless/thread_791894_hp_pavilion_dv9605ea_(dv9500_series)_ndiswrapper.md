---
title: "hp pavilion dv9605ea (dv9500 series) ndiswrapper"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by What_the_deuce on 2008-05-12
Hi there
A friend of mine owns an HP dv9605ea laptop. Interestingly, Ubuntu supports more of the hardware out of the box than XP does, but that's another story.

I installed the broadcom driver from the windows installation directory via ndiswrapper, but alas! no wireless. lspci shows that the broadcom card is there, but ifconfig only gives me ethernet and dialup modem.

Ndiswrapper tells me device present and driver installed. 

Any help appreciated, as I have exhausted all other resources. 

Thank you

---

### Post by Ayuthia on 2008-05-12
> **What_the_deuce said:**
> Hi there
A friend of mine owns an HP dv9605ea laptop. Interestingly, Ubuntu supports more of the hardware out of the box than XP does, but that's another story.

I installed the broadcom driver from the windows installation directory via ndiswrapper, but alas! no wireless. lspci shows that the broadcom card is there, but ifconfig only gives me ethernet and dialup modem.

Ndiswrapper tells me device present and driver installed. 

Any help appreciated, as I have exhausted all other resources. 

Thank you
Can you post the results for:
lsmod|grep -i -e b43 -e bcm43xx -e ssb -e b44 -e ndiswrapper

By the way, which version of Ubuntu are you using (Feisty, Gutsy, Hardy)?

---

