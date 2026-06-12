---
title: "basic wireless questions"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by bioshell on 2006-09-19
Ok, I'm new to Ubuntu, every thing works fine except for my wireless network card that shows up and every thing but I just can't see any wireless Network available from the drop down of the Properties pannel of eth1(which is the wireless card) .. 

How can I fix the SSID to be seen from the eth1 properties pannel ?

Thx in advanced !

---

### Post by happy-and-lost on 2006-09-19
```
sudo apt-get install wifi-radar
```

:D

---

### Post by bioshell on 2006-09-21
Thx for reply h-a-l ! 
I Did installed wifi-radar, and tryed a few things out, but sais it is connected to my router, but router's IP is loop back according to wifi radar.

---

### Post by Melcar on 2006-09-21
Try network manager.
Sudo apt-get install network-manager-gnome (or knetworkmanager if using KDE)
or you can get it from Synaptic.
By the way, what wireless device do you have.  You may have to play around with ndiswrapper or fwcutter to get full functionality on some cards (specially newer ones).

---

