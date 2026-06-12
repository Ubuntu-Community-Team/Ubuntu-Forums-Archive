---
title: "ICS - Ubuntu to Xbox live. NAT problem."
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-10-31
Hello,

I have been using ICS to connect to Xbox Live on the 360.
I run one command to get it up which is.

```
 iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

IPv4 is forward through sysctl.conf
Static IP is made in Network Manager.

wlan0 is the connected to my router (thus the internet).
eth0 is my ethernet card which is connected to my xbox.

Both are fully working!

My problem is NAT.

In the past, I've had NAT as Moderate (Which is what I want) but at the moment, its Strict. 
That means I cannot connect to anyone basically. Moderate works perfectly.

I USED to get Moderate. All the time but for some reason or another, its stopped and now im getting strict. Which is bad :(

Details of wlan0 and eth0 and Xbox.

IP wlan0:
Router: 192.168.1.1
IP: 192.168.1.2
Subnet: 255.255.255.0

eth0:
IP 192.168.0.1
Subnet: 255.255.255.0

Xbox360:
IP: 192.168.0.2
subnet: 255.255.255.0
gateway: 192.168.0.1
DNS works.

I keep getting stict. Why?! I used to get moderate.

I have IPv6 disabled.


Thanks.

---

### Post by Tom--d on 2008-11-01
Anyone?

---

