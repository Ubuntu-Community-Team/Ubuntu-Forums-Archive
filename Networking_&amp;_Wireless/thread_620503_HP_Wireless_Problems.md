---
title: "HP Wireless Problems"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by absol_of_doom on 2007-11-22
Alas, I got an HP m9040n PC, and I'm having problems with its wireless card.
Knetworkmanager recognizes it as a ralink card, but when it tries to use it, the indicator light for the wireless card goes off on the computer, and it doesn't work.
I tried quitting knetwork manager and configuring it in the command line, but it won't work. If I do "ifconfig wlan0 down", then the light comes back on, and if I do "ifconfig wlan0 up", then the light goes back off. Net-setup and iwconfig won't do any good. I have a feeling that it's using the wrong driver. I would try using ndiswrapper, but I can't find any xp drivers for the card. Here is the page on hp for the computer: I can't find anything but vista drivers for the card.
[http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=us&dlc=en&product=3550550&]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=us&dlc=en&product=3550550&")

---

### Post by Capsid84 on 2008-03-05
I'm having the same problem with my HP m9040n too. I can connect to my wireless network but after awhile it will lose the connection and I have to reboot to get it back. I haven't found a solution either :confused:

---

