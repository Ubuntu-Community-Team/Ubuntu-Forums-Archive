---
title: "No LAN with RTL8101E/RTL8102E (Ubuntu 12.0.4)"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by jrgen3 on 2014-09-24
Hello,  I changed from Windows XP tu Ubuntu 12.04 LTS. With Windows there was no networking problem with my HP 625 (RTL8101E/RTL8102E). But under Ubuntu there is no NIC.  Thanks for any help. Jürgen

---

### Post by slickymaster on 2014-09-24
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by varunendra on 2014-09-25
Welcome to the forums jrgen3!

Please open a terminal (Ctrl-Alt-T) and show us the outputs of -
```
sudo lshw -C network
sudo ethtool eth0
egrep -i 'dhcp|dhclient|eth' /var/log/syslog
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

