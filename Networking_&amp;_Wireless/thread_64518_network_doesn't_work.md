---
title: "network doesn't work?"
date: 2005-09-11
forum: Networking &amp; Wireless
---

### Post by AndreAPL on 2005-09-11
hi there. i have, 2 pc conected by lan, one is sharing internet to the other.. but i can't ping it, get same result, neither get any comunication... in windows,all works.
tryed in my debian, network-setup, but still doesn't work,changed hostsname,ip's,servername.... don't know what else can do :mad:

after runing network-setup, my network still doesn't work... don't know what else ... eth0 (192.168.0.3,255.255.255.0,gw 192.168.0.1.. ), and route add default gw 192.168.0.1...
but, when i use route command, i get 192.168.0.0 ?? is this normal ?
can't either ping.
thanks

---

### Post by spd106 on 2005-09-11
Start by checking each of the nics are working and detected. ie lspci, ifconfig, ping 127.0.0.1 (loopback).

Do you have a firewall running? It might be blocking the other pc's connections. 
Firestarter is popular and lets you share internet connection, but it can work in daemon mode and therefore be less obvious.

---

### Post by mlomker on 2005-09-11
Please post the output of:

ifconfig
route -n

---

