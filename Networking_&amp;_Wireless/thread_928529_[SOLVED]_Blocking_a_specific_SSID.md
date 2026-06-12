---
title: "[SOLVED] Blocking a specific SSID"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by redseventyseven on 2008-09-24
Hi everyone, I'm having a minor problem with my wireless network.

My own wireless router is configured properly - SSID has been customised, it's encrypted with a WPA key, generally it's working fine and as I want it. But my neighbours (don't know which ones - I live in a block of flats) have an unsecured router (basically they haven't configured it since it came out of the box - doh!) called "NETGEAR". Occasionally my laptop connects to their router instead of mine.

Apart from the ethical considerations of being connected to someone else's router, I'm also concerned about being connected to a network over which I have no security control. Also, the wireless link with that router is more unreliable than with mine (because it's not in the same flat).

Does anyone know how to configure my wireless card so that it doesn't try to connect to this "NETGEAR" connection?

Many thanks!

---

### Post by lisati on 2008-09-24
Do you have "roaming" turned on? If so, turning it off might be worth a try.

---

### Post by superprash2003 on 2008-09-24
yea,, you could turn roaming mode off and configure ubuntu to only connect to your network.. go to system->admin->network and go to the wifi interface properties and uncheck roaming mode1

---

### Post by redseventyseven on 2008-09-26
This would be one way of solving that particular problem, however I take the laptop with me to work in different locations, and I need to be able to access the wireless networks there...

I don't want to "accept one, reject the rest", I would like it the other way around.

---

### Post by redseventyseven on 2008-10-22
Problem solved.

The folder **~/.gconf/system/networking/wireless/networks** contains information on all the wireless access points that have been accessed by the computer. I deleted the folder pertaining to the offending access point, and *voilà* my laptop no longer tries to connect to it.

---

