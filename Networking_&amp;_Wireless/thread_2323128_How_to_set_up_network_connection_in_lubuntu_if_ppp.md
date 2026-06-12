---
title: "How to set up network connection in lubuntu if pppoeconf command is not available?"
date: 2016-05-03
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2016-05-03
I have installed lubuntu 16.04 in laptop but unable to set up network connection. In
 previous version of lubuntu I have used sudo pppoeconf command to set up network
connection. But in this version of lubuntu pppoeconf is not installed and so it appears 
some other command should be used. Can anybody suggest how I can proceed with
setting up wired network connection in my laptop preferably using command?

---

### Post by arroy_0209 on 2016-05-03
I have earlier used the following commands in succession to set up network connection.
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo pppoeconf
and followed the response by pppoeconf. Finally the network connection was set up.
However as I wrote pppoeconf is not installed in the current version of lubuntu. So how do I proceed?

---

