---
title: "Running Ubuntu 8.04 on Asus EEE701, can't use internet. Cable or Wifi not work"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by Stigern on 2008-06-11
Yes, just installed ubuntu on my eee. But I can't even get the cable internet to work. If I click the two black monitors in the upper corner I get a greyed-out checkbox "Wired Network" and I can enter the "Manual Configuration" which is atm enabled as Roaming mode.

So if anyone can help me out here?

And if I click the "Hardware Drivers" option, it says the following Components are In Use:

Atheros Hardware Access Layer (HAL)
Support for Atheros 802.11 wireless LAN Cards

I'm very confused :S

[[IMG]http://img374.imageshack.us/img374/4011/screenshot2en2.th.png[/IMG]](http://img374.imageshack.us/my.php?image=screenshot2en2.png)

---

### Post by steve_pearce on 2008-06-15
(From [https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes))

   1.Shutdown the EeePC
   2.Unplug the AC power
   3.Remove the battery
   4.Reconnect the battery
   5.Reconnect the AC power
   6.Turn on the EeePC

This is a small bug in Hardy which will likely be fixed in the upcoming release.

You will get cabled ethernet. The madwifi drivers you will have to compile etc yourself. This is covered in [https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes) also.

---

### Post by ecosprog on 2008-06-15
Have a look at this site. [http://eee.ricey.co.uk./](http://eee.ricey.co.uk./) I followed the directions and used the script supplied and it sorts out all the issues with 8.04 and the eeePC.

I'm writing this on my eeePC running 8.04 and connecting to a wifi access point in my garden. I've been using 8.04 for about a month on the eeePC and haven't had any issues with it. It even works with my bluetooth mouse.

---

