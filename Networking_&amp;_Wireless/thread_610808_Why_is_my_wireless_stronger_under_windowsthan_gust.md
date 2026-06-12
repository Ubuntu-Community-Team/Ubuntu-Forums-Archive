---
title: "Why is my wireless stronger under windowsthan gusty?"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by pouleternel on 2007-11-12
I get some neighboors signal at home, and gusty doesn't connect, but windows vista does...
under gusty, it's just roaming and establishing first contact, but apparently does not receive IP adress...
under vista, it's a low signal, but works ok...

what acn I do?

---

### Post by weblordpepe on 2007-11-13
The problem most likely isn't the signal strenth, but something else. 
In the terminal, type **lspci | grep 802** and see what comes up. That should show the name of your wireless chip.

Wifi in linux is a little bit of a mess at the moment. Well sorta. It just takes a bit of mucking around with some wifi chips.

---

