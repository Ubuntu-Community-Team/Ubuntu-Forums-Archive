---
title: "Routing to WiFi instread of the cable."
date: 2019-02-20
forum: Networking &amp; Wireless
---

### Post by Hans_van_Leeuwen on 2019-02-20
A laptop is installed with Ubuntu 16.04.5
This Laptop has both an internet connection with a cable (eth0) and WiFi (wlan0).
A connection, from the Laptop, to a website use, by default, the cable (eth0).
When the cable is disconnected, the WiFi (wlan0) is used.
Is it possible to configure Ubuntu on such a way that, for an certain Website/IP-address,
 always Wifi (wlan0) is used, also when the cable (eth0) is connected?

---

### Post by linuxlion2 on 2019-02-21
Can you give the output of the command "route -n" on your Laptop with Ubuntu?

---

### Post by Hans_van_Leeuwen on 2019-02-22
$ route -n
[FONT=courier new]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.7.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.50.1    0.0.0.0         UG    600    0        0 wlan0
192.168.7.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.50.0    0.0.0.0         255.255.255.0   U     600    0        0 wlan0[/FONT]

---

