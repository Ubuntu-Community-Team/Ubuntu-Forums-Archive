---
title: "Linksys wireless-g network problems"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Headstand on 2008-07-28
I recently installed ubuntu to dual boot with windows. My wireless network works fine on xp but in ubuntu: i setup the properties for the wirless connection in network manager correctly with my essid and my wep key, but after applying the interface changes i could not connect to the internet. 
 My router is a qwest m1000 and my card is a Linksys wireless-g PCI network adapter with speedbooster, my driver is BCMWL5.sys. Please help!!

---

### Post by cdtech on 2008-07-28
Have you tried "wicd" ? I use it to connect to my wireless.

---

### Post by Headstand on 2008-07-28
what do you mean by wicd, what is that?

---

### Post by cdtech on 2008-07-28
It's an alternative to Network Manager.

sudo apt-get install wicd

---

### Post by Headstand on 2008-07-28
If i cant connect to the internet in ubuntu, how can i download and install wicd ( keep in mind i can connect in XP)

---

### Post by Ayuthia on 2008-07-28
Have you tried to connect without encryption?

---

### Post by cdtech on 2008-07-28
You could bypass all that wep until you have everything running properly. Just connect your wired eth connection and use that during your configurations. That way you can get on the internet and configure your wireless as well.

I know the frustration....

---

### Post by whodatpat on 2008-07-28
> **cdtech said:**
> It's an alternative to Network Manager.

sudo apt-get install wicd

Is this a terminal comand?  I just tried it and it could not find anything. (sorry for the newbie question but i have the same problem with my linksys card.

---

