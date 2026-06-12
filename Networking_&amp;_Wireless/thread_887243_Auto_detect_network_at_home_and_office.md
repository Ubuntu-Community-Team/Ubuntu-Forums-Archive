---
title: "Auto detect network at home and office"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by kkfok1 on 2008-08-11
Hi, 
I m using Ubuntu 8.04. I have tried to use the network setting (manual network configuration) on the top right status bar to configure a network setting for home use (basically wlan0 with dhcp) and for office use (basically eth0 with a static ip).
 
However, this does not seems working for either environment. I have read couple of threads and some mentioned that in Hardy, the network manager (I think this is the network setting icon) only work for DHCP but not static.

Currently I have to manually change the /etc/network/interfaces to "auto wlan0" when I am at home and to "auto eth0" when I am at office. Further, I have to change the resolv.conf file also since the nameserver are different in each environment.

Appreciate someone can provide a easier (auto detect) solution for this. My expectation is when I am at home and when the wlan0 is detected, the set of ip details (ip address, nameserver, gw, etc) for the wlan0 is used and vice versa, possible ?

thanks

---

### Post by antono on 2008-11-18
> **kkfok1 said:**
> Hi, 
I m using Ubuntu 8.04. I have tried to use the network setting (manual network configuration) on the top right status bar to configure a network setting for home use (basically wlan0 with dhcp) and for office use (basically eth0 with a static ip).
 
However, this does not seems working for either environment. I have read couple of threads and some mentioned that in Hardy, the network manager (I think this is the network setting icon) only work for DHCP but not static.

Currently I have to manually change the /etc/network/interfaces to "auto wlan0" when I am at home and to "auto eth0" when I am at office. Further, I have to change the resolv.conf file also since the nameserver are different in each environment.

Appreciate someone can provide a easier (auto detect) solution for this. My expectation is when I am at home and when the wlan0 is detected, the set of ip details (ip address, nameserver, gw, etc) for the wlan0 is used and vice versa, possible ?

thanks

Check new network manager in 8.10. It works fine for me :)

---

