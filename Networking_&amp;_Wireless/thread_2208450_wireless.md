---
title: "wireless"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by NyteRukh on 2014-02-28
hi i am running Ubuntu 13.10 64 bit...I have the wireless setup and running properly..but i have a problem with one of the connection...first im on a lenova g530 laptop and the public library i go to has free wi-fi...and it was running fine there untill they had a power outage one day...and now i have trouble loading websites. it say's i am connected but i cant load websites and download updates..it is only at the library i go to....wondering if it means i should reset the wireless(which i dont know how to) or what

---

### Post by tomearp on 2014-02-28
Can you browse websites, download updates etc. properly on other wifi connections?

---

### Post by grahammechanical on 2014-02-28
Network manager keeps information on the wireless access points we connect to. Use Edit Connections to delete the wireless connection to that WiFi access point and then make a new connection the next time you go to the library.

By the way, Network Manager thinks it has done it job when we are connected to a Wireless Access Point (router). If the access point is not connecting to the Internet then there is nothing Network Manage can do about except give us a message saying that we are on a local domain and that something called Avahi has now been disabled.

Regards.

---

### Post by NyteRukh on 2014-02-28
yes works fine on all other connections but the library ones..i can load pages, download, and get updates

---

### Post by tomearp on 2014-02-28
I would try grahammechanical's suggestion of deleting the wifi network entry in network manager and recreating it next time you visit. If it still doesn't work after that then it suggests there is a problem with the library's network; not much you can do other than report it to them.

---

