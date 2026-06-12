---
title: "I dont want an IP"
date: 2005-08-22
forum: Networking &amp; Wireless
---

### Post by asimon623 on 2005-08-22
I don't want my eth1 to have an ip but I need to be "up" which I assume means activated but it wont be up if it isn't configured with an ip

---

### Post by Kyral on 2005-08-22
*blink*

You can't be on the net without an IP Address of SOME kind. Even if you are on a network you have an IP Address within that network. Heck, even if you are NOT on a network you have an IP Address, 127.0.0.1

---

### Post by az on 2005-08-22
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)


[http://aboutdebian.com](http://aboutdebian.com)

---

### Post by asimon623 on 2005-08-22
I'm trying to setup chillispot. Right now I have my router hooked up to the internet then a cat5 from that to eth0 on my ubuntu box and then another cat5 into another wireless router. apparently I'm not supposed to have an ip on eth1

---

### Post by sjpwong on 2006-02-14
[QUOTE=asimon623]I don't want my eth1 to have an ip but I need to be "up" which I assume means activated but it wont be up if it isn't configured with an ip[/QUOTE]

$ sudo ifconfig eth1 up

---

