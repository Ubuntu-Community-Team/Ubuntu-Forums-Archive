---
title: "[SOLVED] ndiswrapper freezes hp tx2000z"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by DesiDishoom on 2008-05-28
hey guys, i'm relatively new to the ubuntu world, but i've managed to get it running successfully with full functionality on two other machines at home. but, as hard as i may try, when i try to get the wireless working on this HP tx2000z tablet, it keeps freezing up a few minutes after the network gets connected. It is never the same time after connection, and it's sometimes during the connection stage.

I am positive the wireless card is the culprit because i can install as many other drivers as i want, and as long as i don't get the wireless up and running, and everything runs great. But as i said, once i use ndiswrapper to install the dell drivers  it freezes every time i boot up.

I have the Broadcom BCM4310 (rev 01) card. I am using the updated version (-17) of hardy 8.04, although the -16 kernel did the same thing...

Any help would be AWESOME because vista is annoying the crap out of me, and getting over this roadblock would absolutely make my summer.

---

### Post by DesiDishoom on 2008-05-28
bump...anyone?

---

### Post by prshah on 2008-05-29
> **DesiDishoom said:**
> 
I have the Broadcom BCM4310 (rev 01) card. I am using the updated version (-17) of hardy 8.04, although the -16 kernel did the same thing...

Have you tried using the [fwcutter]("http://developer.berlios.de/project/showfiles.php?group_id=4547") tool instead of ndiswrapper?

---

### Post by Ayuthia on 2008-05-29
The b43 drivers does not work the the 4310 based upon the information in the b43 mailing lists.  You might try this [link]("http://ubuntuforums.org/showthread.php?t=786397").  The guide is for the dv6701us version, but it might work for you because most of the HP laptops seem to be able to use similar drivers.

---

### Post by DesiDishoom on 2008-05-31
thanks for the responses! i actually ended up using the support docs on linux.dell.com, and using the dell drivers, got it work on my HP laptop! thanks again for the replies.

---

