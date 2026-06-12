---
title: "Wireless Driver installed...no way to connect"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by kjantzer on 2008-08-23
Ok, so in network manager the only options I have are a wired and "phone" option. I dont see a wireless option.

That led me to believe the card was not installed. However, I checked several different ways and the cards seems to be installed. 

Every time I get the urge to try Ubuntu again I can NEVER get it to connect to the internet.

What could be the problem?

Thanks,

Kevin


--------------
In case it matters, this time I used wubi, and its on an HP desktop running windows xp with a wireless card.

---

### Post by TenPlus1 on 2008-08-23
It sounds like your card is detected but doesn't have full support in the kernel yet, kinda like my Belkin 54g (rt2500) card...  I had to use ndiswrapper and the winxp driver to get mines working properly until it's fully supported, but it works great :)

Pop into synaptic and install ndiswrapper-common, ndiswrapper-tools and ndisgtk for a small gui to add winxp drivers with...

---

### Post by pfdevil on 2008-08-23
> **kjantzer said:**
> Ok, so in network manager the only options I have are a wired and "phone" option. I dont see a wireless option.

That led me to believe the card was not installed. However, I checked several different ways and the cards seems to be installed. 

Every time I get the urge to try Ubuntu again I can NEVER get it to connect to the internet.

What could be the problem?

Thanks,

Kevin


--------------
In case it matters, this time I used wubi, and its on an HP desktop running windows xp with a wireless card.
Hey I know you said you already established that your wireless card is installed. Can you just check if it is already enabled. Also type ifconfig - check for wlan0. And to make sure everything is inorder type lspci and search for your wireless card.

---

