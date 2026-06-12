---
title: "WIFI on the fritz, how do I fix?"
date: 2020-12-25
forum: Networking &amp; Wireless
---

### Post by ardouronerous on 2020-12-25
I'm running Xubuntu 20.04.

[ATTACH=CONFIG]287624[/ATTACH]

I'm experiencing WIFI fluctuations throughout the day, and on Firefox, I get messages like "server not found" and sometimes it gets disconnected. And these are the speeds that I'm experiencing whenever I get the "server not found" message. It was a struggle to even visit this site due to the disconnections.

Is there a way to fix this? Thanks.

---

### Post by wildmanne39 on 2020-12-25
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by jeremy31 on 2020-12-27
Sounds like wifi power management, in terminal
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

