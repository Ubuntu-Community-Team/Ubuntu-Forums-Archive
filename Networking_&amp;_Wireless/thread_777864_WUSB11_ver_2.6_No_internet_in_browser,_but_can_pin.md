---
title: "WUSB11 ver 2.6: No internet in browser, but can ping and wget"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by TriMenToR on 2008-05-01
Hy there,

Until today I had a problem with my wireless Linksys card (WUSB11 ver 2.6). I managed to install a XP driver with ndiswrapper on Hardy Heron. (Before that I saw the available connections, but I wasn't able to connect to them.)

Some scenarios:
- When wireless is enabled and I use roaming mode (manual) my linux stalls after filling in the network key.
- When I fill in my wireless connection with a static ip and with the network key, I am able to ping to sites. Also wget works, but in firefox it is not possible to load a page. I think this is strange because I can ping to [www.google.com](www.google.com) or its ip. I tried a wget and I downloaded a file from my remote server.

Does anyone know a solution for this (strange) problem? However I need to fill in manual the IP because when I use the automatic configuration my pc stalls (or he still asking the network key over and over again).

Kind regards!

---

### Post by superprash2003 on 2008-05-01
try changing DNS servers. read here [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by markeee on 2008-05-01
tried changing the ns listed in /etc/resolv.conf ?

mark

---

