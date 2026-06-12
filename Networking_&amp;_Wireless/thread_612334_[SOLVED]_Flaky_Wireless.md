---
title: "[SOLVED] Flaky Wireless"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by raichle on 2007-11-13
*edit*
Problem fixed by following Feisty No-Fluff directions for Broadcom cards.  

Thanks!

---

### Post by knowledge_is_power on 2007-11-13
hah um, could you post how/where you found the solution?
in case other people (me?) have this porblem.

---

### Post by raichle on 2007-11-13
I disabled the driver under the Restricted Drivers Manager, rebooted,  and then followed the directions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I noticed immediately that I was seeing twice the amount of networks as before and finally getting 54 Mb/s.   So far, I haven't had my connection drop so I think it's all fixed.

Good Luck!

---

### Post by knowledge_is_power on 2007-11-14
yo, perfect.  Before my card kept dropping me and stalling. (using BCM43xx and fwcutter or w/e) and replaced it with ndiswrapper and bam.  so much better.  I recommend this path for anybody having network problems and a broadcom wireless LAN adapter.

---

