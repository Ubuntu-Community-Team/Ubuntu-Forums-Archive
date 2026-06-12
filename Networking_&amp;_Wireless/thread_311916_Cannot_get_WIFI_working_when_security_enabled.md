---
title: "Cannot get WIFI working when security enabled"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by jpkeisala on 2006-12-03
I am little lost here. I just installed fresh Edgy Eft to my Z60T Thinkpad (Atheros AR5212) but I cannot get wireless working wher there is any sort of encryption on. 
If I disable WEP completely I am able to get IP but when I put key in Network Settings and try again nothing scanning closes and I don't get IP. 
How can I start to debug this?

---

### Post by jpkeisala on 2006-12-04
I solve this!
I had Wireless MAC Filters on in the router. That messed up.

This is how I solve it:
Nice commands for debugging

fconfig
iwconfig
iwlist scan
sudo /etc/init.d/networking restart
route
sudo gedit /etc/network/interfaces
sudo lspci
sudo lshw

And following up this [thread.]("http://ubuntuforums.org/showthread.php?t=265512") 
Now... I am ready for next challenge... WPA

---

