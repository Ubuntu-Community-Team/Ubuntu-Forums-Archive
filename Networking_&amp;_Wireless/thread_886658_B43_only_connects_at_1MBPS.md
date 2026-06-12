---
title: "B43 only connects at 1MBPS?"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by residualbit on 2008-08-11
I have the the b43 driver running for my broadcom 4311 card. When i view the connection info it says it is only connected at 1MBPS. When i try to configure wlan0 in network tools, it says the interface does not exist. Help!

---

### Post by residualbit on 2008-08-11
bump...it seems like everyone is having a variation of the same problem

---

### Post by Cenotaph on 2008-08-11
The b43 has this issue with some cards. 

you could try to install compat-wireless-2.6 from [http://www.linuxwireless.org](http://www.linuxwireless.org) to get the latest b43 which fixed this on my bcm4318. users -> download and follow the instructions. you'll need to get another firmware too. users -> driver -> b43 and follow the instructions again

or

try this guide to setup your card with ndiswrapper:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

or

try the recent broadcom proprietary driver which officially supports your card (might well be the best option for your particular case)
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

