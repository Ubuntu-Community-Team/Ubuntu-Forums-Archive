---
title: "Using wireless card."
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by fluoridw on 2006-08-28
Well I have succesfully been able to install my intel wireless drivers. but would now like to be able to acces wireless points but I don't know what software to use in linux to search for acces points and such.

I hope you can help me find me a program that allows me to.

Thanks in advance

---

### Post by amo-ej1 on 2006-08-28
In a console (as root) you could search for accesspoints using *iwlist eth1 scan* where eth1 is the wireless interface (see also man iwlist) and you can configure the connection settings using *iwconfig* (e.g. *iwconfig eth1 essid myEssId key 12345678* to set the essid and the wap key). Later on you can use regular tools (like *ifconfig* and *dhclient*) to set the regular interface parameters.

Another nice tool is *wavemon* to monitor your link status (again in a terminal).

---

