---
title: "Atheros AR9462 works slowly, after upgrade from 17.10 to 18.04"
date: 2018-05-10
forum: Networking &amp; Wireless
---

### Post by ormus2002 on 2018-05-10
Internet works slowly, please help.
I added in attachment results from script.

---

### Post by praseodym on 2018-05-11
Lets try
```

sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

