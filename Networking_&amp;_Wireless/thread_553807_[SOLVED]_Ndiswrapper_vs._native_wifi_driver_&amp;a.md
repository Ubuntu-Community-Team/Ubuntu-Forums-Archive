---
title: "[SOLVED] Ndiswrapper vs. native wifi driver &amp;amp; aircrack"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by smurphy_it on 2007-09-18
Good day.  I have a broadcom chipset wifi card (dell 1390 wireless) based on the bcm43xx driver.  I have found a way to get the native linux driver running (with aircrack support) but it is only 11Mb.  I swapped to the ndiswrapper because of other network computers and faster speeds.  However, the aircrack functionality was lost.  My question is, can you get aircrack to work with ndiswrapper (googling it isn't looking promising) or is there a way to have both functional (like through a fakeroot environment or something) ?

I would like to be able to keep the ndiswrapper as default but would like the ability to use aircrack for testing purposes.  I also would like to be able to do this without removing ndiswrapper totally, then installing the native wifi driver, then swapping back (continuous loop).

Does anyone have any suggestions ?

---

### Post by kevdog on 2007-09-18
aircrack wont work with ndiswrapper period.

You can install both drivers, however in order to use them, you can not load both at the same time, you would have to blacklist the unused driver, remove it (modprobe -r ####) and load the driver you want to use (modprobe *****).

---

### Post by smurphy_it on 2007-09-18
That's right, brainfreeze sorry.  When the native driver is installed (not the one that ships with ubuntu feisty) it replaces the driver for the bcm43xx.  Anytime afterwards, you can just modprobe and un-blacklist it.

Thanks for the quick reply.

---

### Post by sergiom99 on 2008-04-09
smurphy_it,
could you please give me some detailed instructions? I am now in the same situation.
Thanks!

---

