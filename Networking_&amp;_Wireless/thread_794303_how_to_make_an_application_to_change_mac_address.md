---
title: "how to make an application to change mac address"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by the_bloods_city on 2008-05-14
how to make an application to change mac address
because every time i restart the pc the mac address return to the original
so i want to make file like (.bat in windows )and put these lines on it 

ifconfig wlan0 down
ifconfig wlan0 hw ether XX:XX:XX:XX:XX:XX
ifconfig wlan0 up 
                                      
:guitar:

---

### Post by az on 2008-05-14
Switch to manual configuration of your network card, then edit /etc/network/interfaces and add a line like this at the end of your eth0 stanza (if indeed eth0 is the device you want to use)

hwaddress ether 00:0b:6a:3a:30:a6

---

