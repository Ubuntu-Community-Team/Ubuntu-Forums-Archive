---
title: "NetworkManager not showing Wireless"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by kandarz on 2007-01-04
I recently got a new laptop and installed Edgy on it along with ndiswrapper drivers for the Dell 1390 minipci card.  Everything is great on it, it will connect to my WPA(1) network just fine.  The one nitpicky thing that doesn't work is NetworkManager doesn't show any wireless at all.

Does anyone know of a reason why it wouldn't show a working wireless connection seeing as iwconfig shows that is connected and iwlist scan seeings my AP?

I use my laptop both at home and at school and would like to be able to switch between wired and wireless networks for transfering files.  Plus away from home and school it does give a nice interface to browse hotspots.

Thanks in advance.

---

### Post by biovore on 2007-02-13
Try it with root permissions..  There are a few people having problems with it..
I'll post back when I figure out what I did.. (I have it working here with a intel wireless)

---

### Post by CCBalla10 on 2007-02-14
> **kandarz said:**
> I recently got a new laptop and installed Edgy on it along with ndiswrapper drivers for the Dell 1390 minipci card.  Everything is great on it, it will connect to my WPA(1) network just fine.  The one nitpicky thing that doesn't work is NetworkManager doesn't show any wireless at all.

Does anyone know of a reason why it wouldn't show a working wireless connection seeing as iwconfig shows that is connected and iwlist scan seeings my AP?

I use my laptop both at home and at school and would like to be able to switch between wired and wireless networks for transfering files.  Plus away from home and school it does give a nice interface to browse hotspots.

Thanks in advance.

dunno if you did this, but had to do it one mine....if you right click on the icon up in your system tray...make sure that wireless is checked...took me a lil bit to figure this one out lol

---

### Post by Nakkis on 2007-02-14
Also, you need to disable the connection from network-admin to make it work with NetworkManager.

---

### Post by industrialpunk on 2007-06-05
In Debian you need to add yourself to the "netdev" group to be able to control the network devices through networkmanager as non-root, otherwise the devices don't show up. Similarly "powerdev" group allows control of power options with some applets.

---

