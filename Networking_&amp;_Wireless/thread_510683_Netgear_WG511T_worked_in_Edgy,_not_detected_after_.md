---
title: "Netgear WG511T worked in Edgy, not detected after upgrade to Feisty"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by rainwalker on 2007-07-26
I just finished upgrading from Edgy to Feisty, and everything seemed to go fine up until I restarted my system. My Netgear WG511T, which worked out-of-the-box in Edgy, isn't detected. Or if it is, it's just not working. The only reason I think it might even be detected is because one of the lights is blinking on and off, but I don't know if that's just because there's power going to it.
I've searched the forums and I haven't been able to find a solution. Is there a driver I need to install for it to work in Feisty?

---

### Post by rainwalker on 2007-07-26
Okay, so in the "Restricted Drivers" window, 3 things are listed:
ATI accelerated graphics driver
Atheros Hardware Accesss Layer (HAL)
Lucent/Agere linmodem controller driver

The latter two drivers are said to be enabled, but their status is "Not in use"
I'm assuming they're for my wireless card, so why aren't they being used if they're intalled/enabled?
Also, before I could even access the "Restricted Drivers" thing, I had to install the package "linux-restricted-modules-2.6.20-16-386". Isn't that something that should have been installed when I upgraded?

I can connect perfectly with an Ethernet (wired) connection, if that matters.

---

### Post by rainwalker on 2007-07-26
Whoa!
I restarted my computer after installing that ATI driver, and now my Netgear card is acting normal (both lights blinking at the same time, means it's connected) and in the "Restricted Drivers" window the Atheros driver is now in use! That third one is still not in use, but I don't actually know what it is or what it's for, so...yay?

Still, I can't help but wonder: 
If I had to install that package to use the restricted drivers, what else wasn't installed during the upgrade?

---

