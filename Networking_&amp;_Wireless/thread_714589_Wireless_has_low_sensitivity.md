---
title: "Wireless has low sensitivity"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by lsuengineer on 2008-03-04
Since I switched from Vista to Ubuntu 7.10 my wireless card has a much harder time connecting to wireless networks. If the signal is just slightly low the wireless will not connect. In the same circumstances Vista would connect to lower wireless signals. I have a Broadcom 43xx and I am using the restricted driver for the Broadcom 43xx chipset which came with Ubuntu. It connects and is very fast with my home network and places such as school but will not connect to signals which are slightly lower such as at a large coffee shop. It seems as though the sensitivity is a software problem since it worked better in Vista.

Thank You

---

### Post by jrusso2 on 2008-03-04
I noticed this too at my job on the far side of the building away from the wireless access point I can only use the wireless in Windows in Linux it will not connect.

---

### Post by lsuengineer on 2008-03-04
Is this a common problem or is it just the imperfection of the Broadcom drivers in Linux?

---

### Post by sofamensch on 2008-03-04
Maybe the topic is not too well chosen for getting the right people in this thread but well i found ya.

I use a different driver, madwifi on an atheros card. Very same problem here - in windows i get good connections with 500kb/s downloads on xp, and just seconds later or earlier with everything else still the same i get max 50kb/s under ubuntu.

I probably try the new madwifi 0.9.4 driver but i cant find a DEB and the Sources didn't work for me, compiling gave a lot of errors ..

---

### Post by uberlube on 2008-03-04
I have a broadcom chip in my compaq notebook and it works really well for me, even on the go. Perhaps you need to install the drivers using ndiswrapper rather than relying on the restricted driver manager. Just a though though.

---

