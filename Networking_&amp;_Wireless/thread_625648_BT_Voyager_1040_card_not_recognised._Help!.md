---
title: "BT Voyager 1040 card not recognised. Help!"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by mcaville on 2007-11-28
I'm just about to make the switch from XP to Ubuntu, but when i ran the OS from disk it failed to pick up my wireless connection.

I'm running a BT Voyager 1040 PCI Wireless card to a BT Vayager 2100 hub. After scanning the forums it seems that others have encountered the same problem, but no sollution was ever offered. Does anyone know if  there is a way to make this card compatable with Ubuntu??? If not, i guess i'll have to stick with XP untill i can afford to purchase a new one.

---

### Post by benson444 on 2007-11-28
Hey mcaville,

I have the same hardware. My router is the Voyager 2100, and I've connected to it with Gutsy Gibbon (7.10) using the Voyager 1040 card. What you need to do is connect the machine by ethernet to enable a download of the bcm43xx driver. The restricted driver manager will pop up when you first boot and ask if you want to install it. I can't remember if I had any messages about the card using the Live disc... I just remember installing Gutsy and the restricted driver manager on rebooting.

Ubuntu isn't installed on that PC any more though, so I can't help troubleshoot any problems you may have. It should work fine though. It just downloaded the driver and installed it. I then clicked on the network-manager icon at the top right, put in the details of the network and it connected first time. Using WPA too.

---

