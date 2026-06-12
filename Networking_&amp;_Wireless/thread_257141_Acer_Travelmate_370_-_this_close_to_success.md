---
title: "Acer Travelmate 370 - *this* close to success"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by jpfreely on 2006-09-14
Hi everyone.

So first of all, please please remind me to never buy an Acer laptop again! I think I'll settle for a nice Lenovo or something next time.

Ok, so here's the story. I really want to run only Ubuntu on my laptop - I've realised that on my laptop there's nothing I need that I can't get from Ubuntu and besides there's no way this thing's going to manage Vista.

The one snag is the wlan. It has a supposedly ipw2100 compatible card, but it seems to be somewhat non-standard; for example in Windows it doesn't work with generic drivers, only the acer ones. Same thing seemingly in Ubuntu - ipw2100 recognises the card but doesn't allow me to change anything. For example telling it to scan networks comes back with operation not permitted.

So instead I deleted the ipw2100 module and instead installed ndiswrapper to use those Acer drivers. I've combined this with acerhk which is meant to enable the wlan hardware - without this little utility my WiFi light stays off. So now under /etc/modules I've got a file called ndiswrapper which loads the windows drivers and a file called acerhk which loads that module and sets the parameter under /proc to turn on the hardware.

This seems to work since the light comes on and network manager lists the access point I'm wanting to connect to. It also tells me the encryption status and the signal strength no problem, as does iwlist eth1 scanning.

BUT upon telling the network manager to connect, it tries and tries but nothing happens. I've tried turning off encryption (scary!) but this also doesn't work. The interface seems to be in a sort of nevernever land since while it's seen by ifconfig -a, iwconfig, iwlist and the network manager if I try to tell ifconfig, ifup or ifdown to do anything with eth1 they tell me the device doesn't exist.

Any help as always is very much appreciated. If you want my /etc/network/interfaces or anything else just let me know.

---

