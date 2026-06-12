---
title: "Weird ssh probplems to do with ip address"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2006-07-17
Hello i have a network of computer with ips of 

192.168.1.1
192.168.1.2
192.168.1.3
192.168.1.4
192.168.1.5 

and thr 192.168.1.1 is the router and 192.168.1.2 is the server they all use ssh exe[t for 192.168.1.4 (windows) and for some reason if i create a ssh to the .168.1.2 computer it will say it cant find it but if i change the ip to 192.168.1.200 it will work but i want them to stay the same becuase i dont want to change all the other computer does anyone no why that would be

---

### Post by Soarer on 2006-07-17
If an IP address works (i.e. you can connect to it) I am forced to assume that it exists :). So I think 192.168.1.200 is assigned to one of your computers.
I suspect that your computers do not have the IPs you think they do, perhaps because they have DHCP client running which has overidden your fixed IP settings.

---

