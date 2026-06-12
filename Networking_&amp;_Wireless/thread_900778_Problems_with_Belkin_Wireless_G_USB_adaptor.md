---
title: "Problems with Belkin Wireless G USB adaptor"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by dude87 on 2008-08-25
I am trying to install Ubuntu 8.04 on a PC and use a Belkin Wireless G USB adaptor.  I've followed the guides available in the forums for configuring a wireless adaptor and had no success.  When I try typing lshw -C network the output gives a logical name to my adaptor (wlan0) but doesn't list a driver.  I tried enabling the Ralink RT2570 driver, which appears to be successful but still no luck.  After enabling the RT2570 driver, though, the logical name of the adaptor changes from wlan0 to rausb0 but there is still no driver listed and I cannot connect the card to my wireless network.

What should I try next?

---

### Post by tuxxy on 2008-08-25
Which adapter is it, the **F5D7051UK **should run out of the box, you may need ndiswrapper if its different to that model

---

### Post by dude87 on 2008-08-25
It's an F5D7050A adaptor, version 2.xxx.

---

### Post by cerebus1707 on 2008-10-20
I have the same adapter and am very new to ubuntu. if there was a very specific step by step giuide, that would help tremendously. 

p.s. i am running on ubuntu 7.1 if there is a difference in how it would work.

---

