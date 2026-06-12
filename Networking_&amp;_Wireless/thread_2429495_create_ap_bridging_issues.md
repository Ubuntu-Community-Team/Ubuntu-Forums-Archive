---
title: "create_ap bridging issues"
date: 2019-10-18
forum: Networking &amp; Wireless
---

### Post by rhine2 on 2019-10-18
**I am not able to directly communicate between clients on the same interface at all.**
**If I use the create_ap command on our router to setup the WiFi interface and connect to it with multiple devices, here is what happens:**
*** I can connect from any client device to the external internet.**
*** I can ping the router from any client.**
*** I can ping any client from the router.**
*** I cannot ping one client from another client.**
 
**So it seems like there is some issues with routing within the subnet. When I try to ping from one client to another I can see that the ARP request makes its way to the router but is not propagated to the other client device. Any tips on what to look for would be appreciated.**

---

