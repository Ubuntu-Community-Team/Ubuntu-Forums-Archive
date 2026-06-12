---
title: "[SOLVED] wireless signal strength in linux"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by TDragon on 2008-08-10
*~Using the latest release of Ubuntu~*
 
 
I have a draft-N wireless adapter (DWA-552) from d-link, I had to use the madwifi drivers in order to gain wireless functionality (could not successfully get on the internet with the ndiswrapper).
 
However, i noticed one thing that has confused me. Ifconfig states that I have 4 adapaters: eth0, lo, **[COLOR=red]wifi0, and wlan0[/COLOR]** (madwifi bound).
 
By default, i usually drop unused connections from ifconfig, including eth0. When I drop wifi0 connection (which automatically appears when driver is loaded), my signal goes up to about 98%, where it should be (this is what I typically see in Vista & XP). However, I loose internet functionality. Therefore, wifi0 must be enabled to get it back. Upon which, my signal drops down to 38%, if not less.

[LIST]
[*]Can anyone shed some light on why this is happening, or in fact that my signal is dropping. If its not correct, is there a way to correct the signal strength meter?
[*]Also, my driver (madwifi) occassionally stops working (every couple of restarts or so), and I am forced to uncheck and recheck the driver in the driver mgr. Is there a way to fix this or is there a better one?
[/LIST]

---

### Post by TDragon on 2008-08-11
*bump*

---

### Post by kdorf on 2008-08-12
> **TDragon said:**
> I have a draft-N wireless adapter (DWA-552) from d-link

Don't take this the wrong way, but that's your problem.

I don't think this is a Linux issue, rather a driver one. In that case you can try using ndiswrapper or finding another version of your driver.

That would be your best bet, I think.

---

### Post by TDragon on 2008-08-12
> **kdorf said:**
> Don't take this the wrong way, but that's your problem.
 
I don't think this is a Linux issue, rather a driver one. In that case you can try using ndiswrapper or finding another version of your driver.
 
That would be your best bet, I think.
 
 
If you took a look above, you would see that I was not able to get on the internet successfully with ndiswrapper. In fact, it was causing the OS to become occassionally unstable.

---

### Post by TDragon on 2008-08-12
According to this thread, these Ubuntu mac users are using another driver based off of the ath9k source. Apparently, this driver is capable of 802.11n. How true this statement is, I don't know. However, I may give it a shot.
 
[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k) <- Driver website
 
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097) <- Thread
 
 
I going to try to get some more info on the driver from the users on that thread.

---

### Post by TDragon on 2008-08-14
Given that I decided to go the route of using that ath9k driver for "actual" 802.11n support, I am marking this thread as solved.

---

