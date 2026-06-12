---
title: "looking for 802.11n conectivity ,Hardy"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by bilbobagins on 2008-07-31
Hi.
 Does anyone out there had any luck with finding a card /drivers etc for 802.11n standard.I seems Atheros do do one and its Linux compatible but had no luck at present tracing one. all this is I`m getting the new BT home hub which can run that standard.at present, I run a Belkin 4318 and Wicd.
Any suggestions please.
              Bilbo.

---

### Post by TDragon on 2008-08-11
> **bilbobagins said:**
> Hi.
Does anyone out there had any luck with finding a card /drivers etc for 802.11n standard.I seems Atheros do do one and its Linux compatible but had no luck at present tracing one. all this is I`m getting the new BT home hub which can run that standard.at present, I run a Belkin 4318 and Wicd.
Any suggestions please.
Bilbo.
 
 
[**madwifi**]("http://madwifi.org/") has drivers that will work with 802.11n, atheros-based cards. However, you will only achieve 802.11g (54mb) speeds (the OS does not support 802.11n at this time).

---

### Post by TDragon on 2008-08-12
According to this thread, these Ubuntu mac users are using another driver based off of the ath9k source. Apparently, this driver is capable of 802.11n. How true this statement is, I don't know. However, I may give it a shot.
 
[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k) <- Driver website
 
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097) <- Thread

---

