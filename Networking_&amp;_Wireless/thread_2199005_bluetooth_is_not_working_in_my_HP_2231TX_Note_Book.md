---
title: "bluetooth is not working in my HP 2231TX Note Book"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by probal21 on 2014-01-11
I am useing Ubuntu 13.04 LTS in my aforsaid note book. But bluetooth is not working...

---

### Post by praseodym on 2014-01-12
Please show these terminal outputs:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
hciconfig --all
```
Did you install
```
sudo apt-get install bluez-utils libopenobex1 gnome-bluetooth 
```

---

