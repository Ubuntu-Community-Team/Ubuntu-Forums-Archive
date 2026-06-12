---
title: "Ubuntu hotspot +30 clients"
date: 2017-09-02
forum: Networking &amp; Wireless
---

### Post by zirwilliam on 2017-09-02
I have ubuntu latest versión. I Need create an hotspot for share files with 30+ clients. 
I now make it [https://youtu.be/Rh-NiRSn6rs](https://youtu.be/Rh-NiRSn6rs)
But i only can conect 10 clients. I dont Need share internet only local files.

---

### Post by praseodym on 2017-09-02
IP address range is big enough?

---

### Post by zirwilliam on 2017-09-02
How can i see it? I am beginer

---

### Post by praseodym on 2017-09-02
Please check

```
cat /etc/hostapd_vlan.conf 
cat /etc/hostapd.conf
ifconfig -a
iwconfig
route -n

```
Since Ubuntu 14.04 WPA2 encryption in such cases is possible, not necessarily working correctly. Try WEP encryption also. We may find the config file limiting to 10 clients?!

Check the hardware and drivers used:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
```
if it is supported at all. It needs support for mac80211/nl80211 subsystem. Alternatively, set up a local router via hostapd

[http://www.linuxwireless.org/en/users/Documentation/hostapd/](http://www.linuxwireless.org/en/users/Documentation/hostapd/)

---

