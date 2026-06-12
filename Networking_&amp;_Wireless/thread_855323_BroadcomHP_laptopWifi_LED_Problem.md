---
title: "Broadcom/HP laptop/Wifi LED Problem"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by btwhite7 on 2008-07-10
I'm having a strange and really annoying problem with my wireless. I have an HP Pavilion laptop with the Broadcom 4318 wireless card but I have it working in Hardy using ndiswrapper and Network Manager. It works great...WHEN I get it working. Here's what happens. After a fresh reboot my Wifi button LED on the keyboard is ON and I can see/scan wireless networks in the vicinity. When I try to connect to my WPA network, it spins and spins and finally fails.
 
But, when I hit the Wifi LED button once, the light goes out, then I hit it again and it lights back up, THEN I can connect with no problem. I can never connect without switching the button OFF then ON. Something isn't getting loaded or something. It's really annoying, but at least it works eventually...any ideas?? :confused:

btw7

---

### Post by silkstone on 2008-07-10
This may be completely unrelated, but there has just been an update to the restricted modules package to resolve an issue affecting wireless on many laptops - mainly Dells but some others as well. The new package has been released today. It's worth running Update Manager and seeing if this patch makes any difference.

---

### Post by btwhite7 on 2008-07-10
It did run some updates this morning but I have yet to reboot...I'll try it.

---

### Post by btwhite7 on 2008-07-10
No dice, same thing.

---

### Post by btwhite7 on 2008-07-10
Does this have anything to do with roaming mode?

---

### Post by btwhite7 on 2008-07-10
Slight update: turning the wifi LED button off and back on isn't the only thing that works, coding in *sudo etc/init.d/networking restart* also works...I know there are ways to run that at start-up, but I don't really want to band-aid it...

---

