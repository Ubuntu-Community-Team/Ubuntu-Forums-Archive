---
title: "Ubuntu 12.04 - Wireless Internet NOT working (Wired connection works)"
date: 2015-09-06
forum: Networking &amp; Wireless
---

### Post by ajith2 on 2015-09-06
Hi , i'm new to Ubuntu.. After installing Ubuntu 12.04 , wireless internet stopped working.My home wifi SSID gets automatically connected everytime my laptop boots , but i cannot access internet wirelessly. However , I'm able to connect to the internet through WIRED connection.

Can anybody please help ?

I'm using a DELL inspiron 1525.

---

### Post by Hadaka on 2015-09-07
Hi,open a terminal ctrl/alt/t and do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
thanks.

---

