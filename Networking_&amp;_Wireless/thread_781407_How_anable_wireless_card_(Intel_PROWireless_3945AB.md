---
title: "How anable wireless card (Intel PRO/Wireless 3945ABG ) in ubuntu 8.04  and R61e"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by grybi on 2008-05-04
How enable Intel PRO/Wireless 3946ABG card in Ibm ThinkPad R61e

It is off, I encountered following Log-Message on Startup:

 ipw3945: Radio Frequency Kill Switch is On:
 Kill switch must be turned off for wireless networking to work.

---

### Post by Paris Heng on 2008-05-04
> **grybi said:**
> How enable Intel PRO/Wireless 3946ABG card in Ibm ThinkPad R61e

It is off, I encountered following Log-Message on Startup:

 ipw3945: Radio Frequency Kill Switch is On:
 Kill switch must be turned off for wireless networking to work.

Just enable the interface of your Intel Pro. Let say your Intel Pro is eth1, substitute the <interface> to eth1.

> iwconfig 

> ifconfig <interface> up

---

