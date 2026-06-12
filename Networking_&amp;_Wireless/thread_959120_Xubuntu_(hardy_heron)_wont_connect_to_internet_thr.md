---
title: "Xubuntu (hardy heron) wont connect to internet through linksys router...?"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by Spea4759 on 2008-10-26
My desktop running Hardy Heron will connect to the internet when directly hooked into my dsl modem, but wont when connected to my linksys wireless g router. The router works for wireless and ethernet, but for some reason my desktop wont connect through it... Any help would be appreciated.

---

### Post by Yashiro on 2008-10-26
So. 

PC<-Modem<-Internet works.
PC<-Router<-Modem<-Internet doesn't?

Make sure the router has DHCP enabled. Admin page on those bricks is usually 192.168.1.1, user <blank>, pass admin.
Make sure Hardy is set to roaming mode (DHCP) in Network Manager.

Attach all the cords correctly and shut EVERYTHING down for at least a minute.
Start it all back up.

---

