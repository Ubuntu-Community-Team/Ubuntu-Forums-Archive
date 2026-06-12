---
title: "Etnernet priority over the wifi ???"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by chphpch on 2016-02-15
Why while connecting Ethernet and WIFI , via a wired adapter receives priority?
 Where in Ubuntu settings, you can change the priority of passing network traffic at the same time included adapters
Ethernet and WiFi ?
Schedule of the monitoring system cacti can be found here
[http://orion-15.byethost8.com/phorum5/read.php?7,75,142#msg-142](http://orion-15.byethost8.com/phorum5/read.php?7,75,142#msg-142)

---

### Post by lensman3 on 2016-02-15
I think what you need to add to /etc/networking/interfaces is the 'metric ###'  The ### is a number that tells the networks attached which one has priority.  I have deleted the network-manager and I don't remember how to change metrics there.  I hand edit the interfaces file otherwise I think that network-manager overwrites this file at every boot.  Each interface can have its own different metric  eth0->44, eth1->45, and so on.

---

### Post by dave157 on 2016-02-15
The link is not english so I can not read that. If you connect the ethernet cable to you system than the wired is the priority. That is how it is on my thinkpad. if I disconnect the wired the wireless is restored. Why would you need both if that is what you want? Ethernet is much faster than wireless, Gigibyte ethernet blows away wireless anyday.

---

### Post by kurt18947 on 2016-02-15
On my machine (Thinkpad T410) if both ethernet & wifi are connected, neither one moves bits properly. i need to disable wireless in order for ethernet to work as expected. It may be possible to use both simultaneously but i don't know how.

---

