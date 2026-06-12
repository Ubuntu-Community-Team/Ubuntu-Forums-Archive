---
title: "Wireless Help:  DWL-650+ and 6.10"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by HeelsFan on 2007-03-19
I installed Ubuntu 6.10 (Edgy) on a IBM Thinkpad R31 and I'm having a little difficulty getting my D-Link DWL-650+ wireless card to function properly.

I have added Network-Manager so that I can easily configure and see available networks.  I am able to view both encrypted and open networks through Network-Manager.  However, once I try to connect to a wireless network, the DWL-650+ card does not connect and the link button stops flashing.

Outside of Network-Manager, I have tried iwconfig and the card does show up and also iwlist shows the networks available.

I'm halfway there (I can see the networks, but can't connect), can anyone post any tips to help me get connected?

Thanks in advance.

---

### Post by Mooie on 2007-03-22
hi, I have a friend with the a ibm thinkpad r31and he cant even get his card recognized, could you explain how you got as far as you did?
he has a post at [http://www.ubuntuforums.org/showthread.php?p=2339092#post2339092](http://www.ubuntuforums.org/showthread.php?p=2339092#post2339092)
thanks

---

### Post by HeelsFan on 2007-03-28
My DLink DWL-650+ card got detected out of the box, but was not able to connect to wireless networks.  I then tried a Linksys WPC11 ver.3 card in the Thinkpad R31 and was able to connect to unencrypted wireless networks (both mine and someone else's in the neighborhood), however things get a little iffy with my encrypted network.  I can connect to the network when it is encrypted, however internet browsing is beyond slow.  Internet speeds are great while connected to a unencrypted wireless network or through an ethernet connection.

The only thing I did was that I installed 6.10 over everything (i.e., did not keep any Windows files).

---

### Post by maximebuy on 2007-04-05
[http://helloubuntu.blogspot.com/2007/04/install-d-link-dwl-650-on-debian-40.html](http://helloubuntu.blogspot.com/2007/04/install-d-link-dwl-650-on-debian-40.html)

should be the same way. edit the /etc/network/interfaces file.

---

