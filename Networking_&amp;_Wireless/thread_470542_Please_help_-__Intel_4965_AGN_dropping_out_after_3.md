---
title: "Please help -  Intel 4965 AGN dropping out after 30 seconds"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by RobotJox on 2007-06-11
Hi, I just bought a laptop with the  Intel 4965 AGN wireless card.

I managed getting it running with ndiswrapper, but the connection stops working after appr. 30 seconds and I have to restart the computer to get it back.

I know Intel is working on a driver, but I would really like to get it running before that.

Any help greatly appreciated!!!

---

### Post by young.seth on 2007-08-13
Hi,

I had a similar problem, the 4965 card was not giving very good performance or was dropping the connection.

I found that the card has power management settings which default to maximum battery life and minimum performance.  If you can access the power management settings of the intel driver then set the property value to *Maximum* for 'Power Management'.

The only problem I have now is that this settings is not persisted between restarts - so I have to set it every time I boot up !

Cheers
Seth

---

### Post by Matthew Wiebelhaus on 2007-08-13
Try the iwl3945 driver maybe

---

