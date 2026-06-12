---
title: "Conceptual questions"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by bobmorning on 2008-05-17
Here's something different for this thread: my wireless works fine (SMC2632 v1, Hostap driver on a IBM thinkpad A22m).

Conceptual why after I insert my pcmcia wireless card and do a iwconfig I get three different logical names:  wifi0 wifi1 and wlan0?

Wlan0 is the only one that will work with dhclient.  

It's a conceptual question and I'm a student of the Linux architecture.  I've googled to no avail trying to find the answer on my own.  

Is there a way to suppress the wifi0 wifi1 naming from being created?

Thanks
Bob

---

### Post by nicedude on 2008-05-17
Some thoughts & info

My wifi for also creates multiples mainly two locations ath0 and wifi0 and only the ath0 is actually used, this is normal behavior for my card and so I just roll with it and it works just fine. So the multiple adapter addresses is less important than whether it works or not. I would recommend you hook your wifi up to an access point and then with a second machine I would run a kismet wireless scanner and verify that only the one interface in your machine is transmitting. Assuming it is the only thing transmitting than I would just go with it and assume that is normal behavior for your card under linux. I found your wifi makers website and a link to your manual for your wireless adapter links are below, so you might read up on your product as well to see if any of this behavior is mentioned.

Good luck and hope the links shed some light on this for you.

Link to the wifi card maker
[http://www.smc.com/](http://www.smc.com/)

Link to your cards manual on their website
[http://www.smc.com/files/AC/MN2632WEN.pdf](http://www.smc.com/files/AC/MN2632WEN.pdf)

---

### Post by kevdog on 2008-05-17
wifi0 is the actual interface defining the card, ath0, wlan0, etc are the virtual interfaces that interface with the actual interface.  I know it seems crazy, virtual, actual, however once you start playing with this concept, its quite useful particularly when attempting to use your card as an access point (monitor mode), or keeping two separate profiles, etc.  If you start using aircrack to use wep, this may be the first exposure you have to the concept of using virtual interfaces.

---

