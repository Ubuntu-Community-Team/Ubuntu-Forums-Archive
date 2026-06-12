---
title: "Wifi Disconnects After System Wakes From Suspend"
date: 2019-07-03
forum: Networking &amp; Wireless
---

### Post by avatarhzh on 2019-07-03
When I suspend my laptop, my internet connection disconnects. The only way to connect it is to reboot. I've tried ```
sudo service network-manager restart
``` and 
```

sudo su
echo 1 > /sys/bus/pci/rescan

```
from searching the forums for possible solutions but neither has worked.

Here's a pastebin link to my wifi info [https://pastebin.ubuntu.com/p/fCD6WZQ6Ww/](https://pastebin.ubuntu.com/p/fCD6WZQ6Ww/).

Can someone please help me with this issue?

---

### Post by gorotman on 2019-07-04
Hi, I've same problem too. I use Ubuntu 19.04 and Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31).

---

### Post by avatarhzh on 2019-07-11
I'm still having problems with this. Can someone please help me with this issue?

---

