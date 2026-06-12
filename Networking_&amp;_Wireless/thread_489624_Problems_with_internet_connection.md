---
title: "Problems with internet connection"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by ayahuazca on 2007-07-01
Hello! 

Just installed the latest version of Ubuntu (7.04 i think) and completed the installation without any problems but i'm having problem connecting to the internet. I used to have no trouble connecting through Windows or on any other computers using Windows. 

I have DHCP on automatic as I usually have and have manually entered a DNS-server using information I got from the other computers connected to the same router. The IP on the computer I'm currently using is 192.168.1.11 and I'm pretty sure the router tries to give the laptop with Ubuntu 192.168.1.12 but it doesn't accept it.

When I run "sudo /etc/init.d/networking restart" in the terminal it says 
```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 196.168.1.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
no expiry time on offered lease
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 196.168.1.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
no expiry time on offered lease
```

...and just keeps on going, changing only the interval to a number between 4 and 7.

Some specs:
Laptop: HP nx7400
Network: Intel PRO/Wireless 3945ABG
Router: Philips SNB6500 Wireless Basestation
Modem: ZyXEL Presige 600

I'm completely new to this OS and I apologise in advance if this has been answered a million times before. Tried the search function but theres just too many different networkrelated issues to go through.

Ideas?

EDIT: 
Forgot to add that I'm trying to connect trough a cable. Step two will be to get the wireless working :)

Also, some more info I can add - when I look at IP Information under Devices in the Network Tools manager and choose Ethernet Interface (eth0) it says:
Protocol: IPv6
IP Address: fe80::217:8ff:fe3d:198d
Netmask/Prefix: 64
Scope: Link

---

