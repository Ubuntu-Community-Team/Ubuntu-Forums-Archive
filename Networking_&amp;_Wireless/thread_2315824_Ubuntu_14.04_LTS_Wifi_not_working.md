---
title: "Ubuntu 14.04 LTS Wifi not working"
date: 2016-03-02
forum: Networking &amp; Wireless
---

### Post by Brendan_Snyder on 2016-03-02
Hi, I'm new to ubuntu and have recently installed Ubuntu 14.04 LTS on my PC. As soon as it was installed and booted up, I realized that although my wifi name is listed, it won't connect. It's not my router as it happens with all connections. I have read many other posts about this problem, but none seem to work. Any help is appreciated. Thanks!

---

### Post by hmiersch on 2016-03-02
Have you tried [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers) ? When I had a similar problem last year, I solved it using that info.

---

### Post by Hadaka on 2016-03-02
Hi,please open a terminal...ctrl/alt/t...then copy and paste..
```
lspci -nnk | grep -iA2 net
lsmod | egrep 'b43|wl|ath|iwl|rt'
rfkill list all
```
post the output..
also please ask a mod to move this to networking and wireless
thanks.

---

### Post by howefield on 2016-03-02
Thread moved to the "*Networking & Wireless*" forum.

---

