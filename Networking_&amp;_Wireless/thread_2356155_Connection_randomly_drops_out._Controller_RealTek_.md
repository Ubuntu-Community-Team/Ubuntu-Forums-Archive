---
title: "Connection randomly drops out. Controller RealTek RTL8723BE Ubuntu 16.10 HP"
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by mr-mister on 2017-03-20
Hi, i've recently installed ubuntu and keep having troubles with wifi connection that disconnects and connects again by itself(noticed also that when it works it's slower than in windows). I've tried some temporary solutions but they won't do the trick. [http://paste.ubuntu.com/24215585/](http://paste.ubuntu.com/24215585/)  this is what wireless info returned. I have connected in two different home network and had basically the same problem. In one forum they suggested sudo modprobe.d/b43 but i don't remember the exact command and i think it just worsted things. Tell me if you need any more innformation, thanks!

---

### Post by praseodym on 2017-03-20
Please check

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot. If its not better try it again with "ant_sel=2" instead

---

### Post by mr-mister on 2017-03-20
Seems to be receiving more signal. No disconnection so far, Thanks a bunch!

---

