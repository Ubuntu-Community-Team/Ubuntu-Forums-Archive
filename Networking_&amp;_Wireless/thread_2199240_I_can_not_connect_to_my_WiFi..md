---
title: "I can not connect to my WiFi."
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by nikolasbsepulveda on 2014-01-12
I dual booted Ubuntu on to my hard drive along with windows 8 and I am unable to connect to my internet. Please help.
I have an external wireless card, specifically Netgear N300. Thanks again!

---

### Post by slaytons on 2014-01-12
What is the output of 

> 
sudo lshw -C network
cat /var/log/syslog | grep NetworkManager


---

