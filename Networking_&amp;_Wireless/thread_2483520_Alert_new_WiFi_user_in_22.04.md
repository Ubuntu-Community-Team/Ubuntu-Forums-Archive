---
title: "Alert new WiFi user in 22.04"
date: 2023-02-01
forum: Networking &amp; Wireless
---

### Post by meetdilip on 2023-02-01
Hi, is there any method to get an alert when a new user joins my WiFi network? Using 22.04.

---

### Post by meetdilip on 2023-02-16
Hi, need some help creating a script for these 2 commands

Trying to run these commands one by one

nmap -sn 192.68.1.0/24

arp -a

store arp -a somewhere, run again and if there is any change, use notify-send 

would be great if I can log the notify-send content. 

Thanks

---

### Post by meetdilip on 2023-02-16
python-nmap has something 

[https://pypi.org/project/python-nmap/](https://pypi.org/project/python-nmap/)

---

