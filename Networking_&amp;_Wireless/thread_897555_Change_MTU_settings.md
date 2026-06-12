---
title: "Change MTU settings"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by MarkUK on 2008-08-22
Just a quick question , how to i change the MTU of my network ? i have read somewhere about sudo gedit /etc/network/interfaces , but not to sure what to put .
Cheers
Mark

---

### Post by caljohnsmith on 2008-08-22
Just add the "mtu <number>" to the end of your card's interface entry in /etc/network/interfaces:
```
iface wlan0 inet static
address 192.168.1.23
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid Home Network
[COLOR="Blue"]mtu 1492[/COLOR]
auto wlan0

```
Your interface entry in the interfaces file will be different if you use DHCP instead of setting up a static IP like I do above. But the point is to put the "mtu <number>" line in there.

---

### Post by MarkUK on 2008-08-22
Thank you :)

---

