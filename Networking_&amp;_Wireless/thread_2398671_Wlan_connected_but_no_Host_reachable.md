---
title: "Wlan connected but no Host reachable"
date: 2018-08-15
forum: Networking &amp; Wireless
---

### Post by najros on 2018-08-15
Hello,
I have one notebook that is unable to realy connect to my wlan router. The network manager shows "wlan connected" but no other computer in the network or in the internet is reachable, not even the gateway.
I have this problem only with this one laptop, all others are working.
I was able to connect that laptop with one single wlan router (unfortunately not the one i need to) after stripping all wlan-router settings down. If I use the default settings of current wlan-routers, I can not even connect to the wlan. Unfortunately the same settings with other wlan routers (especially my own) are not working.
There is no wlan connection available on Ubuntu-Live-System.
Tried already everything I have found on the internet, but with no success.
I run the "wireless-info" script from [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) with attached output.

Thanx for any help!

---

### Post by chili555 on 2018-08-15
What is the response to the terminal commands:```
ls -al /etc/resolv.conf
ping -c3 192.168.2.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```Thanks.

---

