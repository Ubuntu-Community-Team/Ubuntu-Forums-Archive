---
title: "need help installing intel pro/100 ve on hardy heron"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by junxuan on 2008-08-15
can any1 provide me a guide to install my Intel PRO/100 VE wireless card. im using a laptop and i need help setting it up. Hope that i can get some support

---

### Post by chili555 on 2008-08-15
It should work out of the box with a module *e100.* If you open a terminal and do:```
sudo lshw -C network
```you will see if the card has a logical name, eth0 hopefully, and is associated with a driver e100 hopefully. If it is, hook up the cable and do:```
sudo dhclient eth0
```If you do not connect, let's troubleshoot by looking at:```
dmesg | grep e100
```

---

