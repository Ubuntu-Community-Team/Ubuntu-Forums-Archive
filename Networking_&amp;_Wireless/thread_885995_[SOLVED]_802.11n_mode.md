---
title: "[SOLVED] 802.11n mode"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by Java Geek on 2008-08-10
I have a Dlink DWA-552 Windows network card that I am running with NDISwrapper. However, it is only running in 802.11g mode. I would like to be able to run it in 802.11n mode to maximize its capabilities. Is there an alternate method to making it run in 802.11 mode?

---

### Post by PinkFloyd102489 on 2008-08-10
Currently no way to achieve N speeds, especially with ndiswrapper. ndiswrapper is the most restrictive driver available.

---

### Post by Java Geek on 2008-08-11
ok thank you

are there other windows drivers available that might possibly allow my card to do what it needs to do?

---

### Post by TDragon on 2008-08-11
> **Java Geek said:**
> ok thank you
 
are there other windows drivers available that might possibly allow my card to do what it needs to do?
 
 
**I have the same card BTW - w/ a DGL-4500 router.**
 
ndiswrapper is what allows you to run windows drivers in linux. Even with a linux-native driver, **[COLOR=red]madwifi[/COLOR]**, it appears that N is not an option (automatically connects at G).
 
IMO, madwifi is much more stable than using the d-link drivers with ndiswrapper (I actually had to reinstall Ubuntu due to problems).
 
 
> **PinkFloyd102489 said:**
> **Currently [COLOR=red]no [/COLOR]way to achieve N speeds**, especially with ndiswrapper. ndiswrapper is the most restrictive driver available.
 
Java Geek, as you can see, PinkFloyd102489 was basically telling you what I just said.

---

### Post by TDragon on 2008-08-12
According to this thread, these Ubuntu mac users are using another driver based off of the ath9k source. Apparently, this driver is capable of 802.11n. How true this statement is, I don't know. However, I may give it a shot.
 
[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k) <- Driver website
 
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097) <- Thread

---

