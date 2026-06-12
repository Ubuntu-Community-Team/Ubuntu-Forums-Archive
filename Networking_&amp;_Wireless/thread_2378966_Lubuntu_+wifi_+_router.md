---
title: "Lubuntu +wifi + router"
date: 2017-11-29
forum: Networking &amp; Wireless
---

### Post by luisss749 on 2017-11-29
Hello
I recently installed Lubuntu 16.04.3  on a 32 bit desktop PC, now i want to connect this pc to my wifi internet modem, for this i have a linksys WRT54GL router, i want to connect this router to the pc using the ethernet cable, currently i have this connection and i can get access to the setup of this router through the address: 192.168.1.1, now i want to know how to configure this to connect the pc to my existing wifi internet signal/modem, can you help me??
kind regards
Luis Salazar

---

### Post by tentoes2 on 2017-12-12
You need to configure your WRT54G as a client bridge. This will require an alternative firmware such as DD-WRT

---

### Post by cariboo on 2017-12-13
You should be able to connect a cable from your modem/router to the wrt54gl. I have basically the same setup, but I use an 8 port switch and a Linksys router. Be sure to disable dhcp on the wrt54gl. Check out this thread, on how to do it:

[https://community.linksys.com/t5/Wireless-Routers/How-to-set-up-WRT54GL-as-access-point/m-p/38064](https://community.linksys.com/t5/Wireless-Routers/How-to-set-up-WRT54GL-as-access-point/m-p/38064)

---

