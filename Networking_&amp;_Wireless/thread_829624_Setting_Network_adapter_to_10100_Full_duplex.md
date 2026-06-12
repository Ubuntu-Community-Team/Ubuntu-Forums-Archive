---
title: "Setting Network adapter to 10/100 Full duplex"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by Eric the Red on 2008-06-15
For some reason my file transfers from my Xubuntu machine to another machine on the network is stuck at (15mbps) which is = (15/ 8 ) = 3MB/s .. 

I'm using a 100mbps network switch, ( a Linksys WRT54G) which states it can do 100mbps Full-Duplex.. is there a chance that my Xubuntu machine's network adapter isn't set at the right speed? If so, how do I change the speed of the network adapter.. 

In XP.. you would go to your network adapter -> hit properties -> hit Configure -> speed = 100MB full duplex.. 

Any help would be greatly appreciated.

---

### Post by Eric the Red on 2008-06-15
Bump

---

### Post by chili555 on 2008-06-15
Please see *man ethtool.* After consultation, it might be something like:```
sudo ethtool eth0 -s speed 100 duplex full
```You might want to do:```
sudo ethtool eth0
```This will let you review the settings currently in place.

Post back if you get stuck.

---

