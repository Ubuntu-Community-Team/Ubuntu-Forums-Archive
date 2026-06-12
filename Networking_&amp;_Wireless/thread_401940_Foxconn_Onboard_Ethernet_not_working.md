---
title: "Foxconn Onboard Ethernet not working"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by DefinitelyCheese on 2007-04-05
My Ethernet problem regarding my Dapper-Edgy + MB/CPU upgrade was due to a damaged Ethernet cable, nothing else. 
Replaced the cable, Edgy worked fine.   D'Oh!

---

### Post by chili555 on 2007-04-05
As far as I can Google, this uses the Marvell 88E1116 PHY chipset. You might try to verify that with *sudo lshw.* I believe it is supposed to work with *forcedeth*, so you might try:```
sudo modprobe forcedeth
ifconfig
```Since you have two ethernet ports, I think, if the driver finds the ethernet chipset, you may find eth0 and eth1 in ifconfig. If so, simply do:```
sudo dhclient eth0
sudo dhclient eth1
```since you don't know which is connected.

I'm not sure forcedeth support was very good as far back as Dapper, frankly. You might try downloading and burning a Feisty LiveCD to see if you cards are recognized and connect.

---

### Post by DefinitelyCheese on 2007-04-20
Thanks for the info, Chili555.

Ultimately there was no problem with either ethernet port and no problem with Ubuntu, but a damaged cat-5 cable.  Once that was replaced, everything n/w related just sprang to life.  Which was nice.

Still, I appreciate the extra info (A little education makes me want to investigate and learn more) and your time in replying.

---

