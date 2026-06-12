---
title: ":mad: Ubuntu 8.10 wireless support stinks"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by kingleer on 2008-11-09
So, how exactly is ubuntu 8.10 an improvement over 8.04 or even 7.10 in terms of wireless connectivity?

---

### Post by Ayuthia on 2008-11-10
> **kingleer said:**
> So, how exactly is ubuntu 8.10 an improvement over 8.04 or even 7.10 in terms of wireless connectivity?

Based on your other post, you have a Broadcom 4311 rev 01 card.  In 8.10, the card should work out of the box by activating the wl (Broadcom STA) driver in System->Administration->Hardware Drivers.  This driver was available partway through 8.04.  In 8.04, there were some ssh and other secure connection issues where this driver could not connect in 8.04 but it should be fixed now.

You can also use the b43 driver there also, but you still need the firmware just like you did in the past.  This driver has also improved for this card.  It is now just as fast as NDISwrapper or the wl driver.  In 8.04, you were able to get connected, but sometimes the transfer rates would not go faster than 1Mb/s.  In 7.10, this card had a lot of transmission issues where data had to be retransmitted repeatedly.

Finally, the NDISwrapper option is also still available.  The big difference in this driver is the introduction of the b43 driver in 2.6.24 (Hardy 8.04).  The b43 driver needs to have the ssb driver and that created some problems with NDISwrapper.  The ssb driver is a kernel module so it is loaded before the NDISwrapper module.  As soon as it found the cards that it needed, it took them and blocked out the other drivers from accessing the card.  Since NDISwrapper is not a kernel module, it would not work until you unloaded the ssb module, loaded NDISwrapper, and then reloaded the ssb module (if you still needed it).  The only change for NDISwrapper in 8.10 is that if you try to compile NDISwrapper yourself, it will not compile without a patch.  NDISwrapper has not released a new stable version to resolve that issue.

---

### Post by frank_costanza on 2008-11-10
kingleer,

I'm also having problems with my Broadcom 4311. I was really looking forward to a smooth wireless experience with Intrepid, but it didn't happen.

I am able to connect to my router using the Broadcom STA driver. However, it is very inconsistent---sometimes, it'll connect just fine but other times it won't. Also, the Network Manager applet seems to get hung up while obtaining an ip address from the router. Once I'm connected, the wireless is sometimes fast and sometimes very slow. I'm not sure what steps I need to take to troubleshoot. But I may try the fwcutter route to see if that works better.

Under previous versions of Ubuntu, I used ndiswrapper which had problems connecting to the router sometimes, but once connected, was pretty solid speed-wise.

I'll post if I find any solutions. BTW, I'm using a Compaq v3000.

---

### Post by pugz3d on 2008-11-12
I'm actuall very impressed with the Intrepid install experience.  I installed on my Latitiude D620, and didn't have to fight with ndiswrapper and modprobe, etc....  I did notice the Update Manager only ran at 20kbps, but hey my wireless worked out of the box.  I was astounded after the nightmare I had with b43 drivers and what not on a Latitude X300.  I fought for probably almost 10 hours to get a 4306 running on the x300 until I found out I had another card and got it going.  My D620 has a 4311 rev 01.  If anyone has any tips to tweak the speed that'd be great, but for casual browsing it's functional.

UPDATE: Just ran a speed test at dslreports.com and got 1800kbps, so maybe the update servers were just slow last night.
Transmission is topping 600KB/s also, so maybe the STA driver is doing me solid.

---

