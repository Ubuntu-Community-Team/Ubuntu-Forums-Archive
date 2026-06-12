---
title: "Wifi RT2561/RT61 keeps reconnecting."
date: 2016-10-30
forum: Networking &amp; Wireless
---

### Post by korotkovd on 2016-10-30
Running from iso kubuntu-16.10-desktop-amd64.iso. Connected to home wifi and wifi keeps disconnecting and reconnecting.Debian 8 works well with it.I've seen others in the forum with similar problems but I can't fix the problem.Appreciate any advice. Thanks in advance.

---

### Post by jeremy31 on 2016-10-30
I suspect power management issues
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart NetworkManager.service
```

Check ```
iwconfig
``` to see if power management shows off

---

### Post by korotkovd on 2016-11-01
It works! Thank you.How do you think, why is this option not disabled by default?

---

