---
title: "wireless connection problems"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by joeya42 on 2008-10-03
Hi, brand new to Ubuntu. Have installed on my Asus 6000 notebook. Wireless is not starting and can not get on to interenet ar retrieve mail. Seems to be a common problem but not understanding how to fix. Can someone please give me basic: instructions as I love Ubuntu but cant get online.:

---

### Post by Crafty Kisses on 2008-10-03
I'd like to see these commands:
```
sudo ifdown wlan0
sudo ifup wlan0
```

You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
/var/log/messages

```

---

