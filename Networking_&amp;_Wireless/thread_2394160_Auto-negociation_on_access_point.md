---
title: "Auto-negociation on access point"
date: 2018-06-13
forum: Networking &amp; Wireless
---

### Post by yayou on 2018-06-13
Hi everybody,

I would like to know if some access points have the ability to use protocols (802.11g or 802.11n) according to devices capabilities or if they can only choose one mode according to the least advanced devices for better compatibility. For example, if I have an access point supporting 802.11bgn, 1 laptop with 802.11n NIC and another with a 802.11b NIC, will the access point automatically use 802.11b for the both of them? Or is it possible for him to use 802.11n for the first laptop and 802.11b for the second at the same time?

Thank you for having read.

---

### Post by TheFu on 2018-06-14
802.11b will slow down all other connected devices.  At this point, only 802.11n and newer devices should still be used.  Even "g" devices have a drastic impact on performance and available air-time.

You can solve this by having 2 APs - one only for the older stuff. and the other only for the new stuff.  Just be certain to prevent new devices from connecting to the slower talking ones and prevent the newer APs from allowing slow-talking devices.

Just because you can do something, that doesn't make it a good idea.

---

### Post by yayou on 2018-06-20
Thank you TheFu and I deeply loved your last phrase. The world would be very much wonderful if most people had this in mind. About the actual question, I started to think of this possibility but would it still work as expected if we connect the for-old-stuff AP with the for-new-stuff AP. I ask this question because all those type of devices will still need to access internet and will ended being connected in one way or another. For example, if the for-old-stuff AP is a 802.11b/g/n AP connected by ethernet cable to the for-new-stuff AP which is a Wifi modem/router of 802.11ac only receiving the internet signal. Do you think that we will still have a network in which 802.11ac laptop won't be slowed down by the older type of devices?

---

### Post by TheFu on 2018-06-20
Buy a $7 USB 802.11ac adapter and disable the built-in 802.11b stuff on the old laptop 
OR 
use two different APs with wired connections into the network.  Make certain the APs are on different, non-interfering, channels.

---

### Post by mörgæs on 2018-06-20
> **TheFu said:**
> Make certain the APs are on different, non-interfering, channels.

+1

The for-new access point can be set to run on 5 GHz only. The more traffic moved away from 2,4 GHz the better.

---

### Post by TheFu on 2018-06-20
5Ghz doesn't go through most building materials, but for line-of-sight connections it can be much,much,faster.

---

### Post by chili555 on 2018-06-20
> **yayou said:**
> Hi everybody,

I would like to know if some access points have the ability to use protocols (802.11g or 802.11n) according to devices capabilities or if they can only choose one mode according to the least advanced devices for better compatibility. For example, if I have an access point supporting 802.11bgn, 1 laptop with 802.11n NIC and another with a 802.11b NIC, will the access point automatically use 802.11b for the both of them? Or is it possible for him to use 802.11n for the first laptop and 802.11b for the second at the same time?

Thank you for having read.Test it for yourself. 802.11b is limited to 11 Mbps and is further limited by the distance from the router, interference, etc. Do a speedtest at [http://www.speedtest.net/](http://www.speedtest.net/) with each and every device connected on your network. Do any of them get a result higher than 11 Mbps?

TheFu and I will be most interested in the result.

---

### Post by TheFu on 2018-06-20
Chilli - did you make it to SELF this year?  Zack had a great talk about the different wifi standards and JimS brought his vast wifi knowledge from his Ars articles as "the peanut gallery."

Both agreed.   Anything slower than 'n' wasn't worth the effort to allow.  Put up an old, slow AP for those devices and forget about it.

---

### Post by chili555 on 2018-06-20
> **TheFu said:**
> Chilli - did you make it to SELF this year?  Zack had a great talk about the different wifi standards and JimS brought his vast wifi knowledge from his Ars articles as "the peanut gallery."

Both agreed.   Anything slower than 'n' wasn't worth the effort to allow.  Put up an old, slow AP for those devices and forget about it.I missed it. I had it on my mind to attend as it was but 15 miles or so from Casa Chili. I would have enjoyed it.

---

