---
title: "pcap.h : no suitable device found"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by seniorece26 on 2008-04-17
Hi,
I need a way of capturing packets that are coming from a particular device, the MAC address of which I know. First of all,  the pcap_lookupdev() function does not return any suitable device. My interface is eth1. the c-program to find the suitable devices for packet capture does not return anything. What can be the reason for that?

Moreover, my understanding of sniffing so far has led me to conclude that there is no way of detecting packets coming from a particular device. If there is, can anyone, please, direct me how to do that. 
this is my first post on this forum. I hope I am at he right place. 
Any help is deeply appreciated.

thank You
Umair

---

### Post by althoughX on 2008-05-14
I also had same problem.
Run your program as root,

gcc program.c -lpcap -o program.out
sudo ./program.out

then, it works now

---

