---
title: "Creating an access point"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by OBELIKS on 2006-08-18
Hi!
I'm making myself an AP with one wireless connection and one wired connection. I managed to get wired connection working, but with the wireless adapter I cant seem to get the connection.
I'm using edgy-server with shorewall.
How should /etc/network/interfaces look like for wireless? Should it be in master mode or something else?
The adapter is Canyon CN-WF511. And iwconfig shows wmaster0 and wlan0.

---

### Post by kb3hkg on 2006-08-18
To be an AP it should be in master mode. You will almost definitely want DNSmasq and probably IPmasq running as well, not having them causes headaches

---

### Post by OBELIKS on 2006-08-18
I'll need more instructions than that :D Basicly it would be nice just to get those two computers to ping.

---

### Post by OBELIKS on 2006-08-20
Ok, I have tried the following
I modified the /etc/network/interfaces like this
```
auto wlan0
iface wlan0 inet static
        pre-up /sbin/iwconfig wlan0 mode master essid pero channel 9
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
``` 
and restarted netwtorking, wlan0 goes to master and it does change the ip and netmask but the laptop does not detect it. What am I doing wrong? I just want to get server and laptop to ping. After that i thing that I can manage with shorewall.
The card has Ralink rt2561st chip on. how can I check if the drivers are working ok? I tried to use the latest CVS rt2x00 drivers but it just gives errors and computer does not even boot.

---

