---
title: "one more strange network problem"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by heartsmagic on 2006-12-07
First of all i searched the forum and read all the related topics about that, also i looked at some mail lists about ubuntu. I tried lots of thing but still there is the problem. 

Time to time i loose my network connection, i mean i cant surf the net but i can use IRC, Azureus. I cant ping anywhere so i dont think so this is a DNS problem. I edited resolv.conf, manually enter DNS (i knnow it is overwritten but i foreced it not to be) , i edited dhclient.conf, i tried static ip. Now it seems there wasnt any problem till i used aptitude update, whenever i use this my problem starts again. No ping, no surf, aptitude update returns connection error, after a couple minutes, net comes back.

Note: ipv6 is off for firefox.

---

### Post by Iowan on 2006-12-11
> **heartsmagic said:**
>  i edited dhclient.conf
What did you change?  Did you edit the "prepend" line, remove the "domain-name-servers" from the "request" line? Both?

---

