---
title: "Route web traffic between subnets with different ports"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by peap on 2013-11-27
In short: How do i forward incoming eth0/wlan0 port 10.0.1.25:8080 to outgoing eth1 192.168.1.1:80? 

On this box I have a web service running on a usb stick (huawei E3231 modem) available at 192.168.1.1:80. The device is recognized as eth1 and has ip 192.168.1.100.
I wish to direct incoming web access to port 8080 on the other NIC's (eth0 and/or wlan0) to 192.168.1.1:80 so that I can access the web GUI of the modem from anywhere in my network. Theoretically this should be easy but I'm not getting anywhere and this is my first close encounter with iptables.

192.168.1.100 : ip of eth1 on the box (the usb dongles' built-in NIC)
192.168.1.1    : ip of the web service of the dongle
10.0.1.25        : ip of the wired eth0 of the box
10.0.1.24        : computer trying to access 10.1.1.25:8080 through browser
10.0.1.1          : default gateway

I've tried these lines and a bunch of variations of the iptables command but I'm not getting anywhere. 
```
sudo sysctl net.ipv4.ip_forward=1
sudo iptables -t nat -A PREROUTING -p tcp -d 10.0.1.25 --dport 8080 -j DNAT --to 192.168.1.1:80
```

I'm in a little bit to deep here, is this the correct approach or should i do some "route add" perhaps?

---

