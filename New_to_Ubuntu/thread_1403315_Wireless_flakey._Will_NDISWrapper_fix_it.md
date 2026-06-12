---
title: "Wireless flakey. Will NDISWrapper fix it?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by mdsmedia on 2010-02-10
Hi all,

Haven't posted or been reading for a while.

Up until now my Wireless has been flawless. I'm not sure if it's Karmic or my hardware. Hoping NDISWrapper will provide the solution.

I have a DLink Wireless router, but I've plugged in my previous Wireless interface and used it as my connection to the router. So I have a router with wired and wireless capabilities and plugged a wireless antenna to it, and it's now flaky.

I'm struggling to get WPA or WEP settings on the DLink to marry with the Ubuntu network manager, so I just connect with the old Wireless antenna, which is wired to the DLink.

Wondering if the Wireless connection between my Toshiba Satellite Pro and the Antenna might be flaky due to software and NDISWrapper might fix it.....have never needed NDISWrapper before.

---

### Post by candtalan on 2010-02-10
Can you revert to the conditions when you had no problems?

> 
I've plugged in my previous Wireless interface and used it as my connection to the router. So I have a router with wired and wireless capabilities and plugged a wireless antenna to it, and it's now flaky.

What was the reason for doing this?
It sounds as if the changes here are causing problems. 

I have doubts whether software will improve things, but ndiswrapper - it uases the windows driver - you tell it where the windows driver is located -  can be tried and removed if you decide differently later. 

Sorry I can't help more.

---

### Post by mdsmedia on 2010-02-10
> **candtalan said:**
> Can you revert to the conditions when you had no problems?



What was the reason for doing this?
It sounds as if the changes here are causing problems. 

I did that when I first got the modem/router, to get a clearer line between my laptop and the antenna. It didn't cause problems in previous releases of Ubuntu, and it's fine in Windows. That's why I thought it might be an issue with Wireless drivers in Karmic and that NDISWrapper might help.

I'll give it a try. Thanks.

---

