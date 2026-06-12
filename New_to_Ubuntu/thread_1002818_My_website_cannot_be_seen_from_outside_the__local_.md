---
title: "My website cannot be seen from outside the  local network"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Atingueli on 2008-12-05
Hi,
SOS
I've set up a working DNS, and registered my own DNS domain. I have implemented as well the web server. From my local network, everything is perfect, everyboby can browse the website. My problem is: from outside the local network it is not possible to access the website, I've configured the CNAME records on the DNS, but still nothing is working from outside. Please advise me how can I make it work.???????????

---

### Post by overdrank on 2008-12-05
Moved to  Absolute Beginner Talk  :)

---

### Post by bodhi.zazen on 2008-12-05
> **Atingueli said:**
> Hi,
SOS
I've set up a working DNS, and registered my own DNS domain. I have implemented as well the web server. From my local network, everything is perfect, everyboby can browse the website. My problem is: from outside the local network it is not possible to access the website, I've configured the CNAME records on the DNS, but still nothing is working from outside. Please advise me how can I make it work.???????????

First guess is you need to forward port 80 from your router to your server.

Second guess is it can take some time for DNS changes to take effect, if this is a new set up it can take 24 hours to propagate.

Third guess is a firewall on the sever.

If this is still not working, call your DNS tech support, most of them are very very helpful, or provide additional information on what you have done to set your DNS and LAN.

---

