---
title: "Wireless disconnects without a reason and stops working"
date: 2017-09-08
forum: Networking &amp; Wireless
---

### Post by chief096 on 2017-09-08
Hi guys, sometimes I have troubles with my wireless connection, that disconnect and not reconnect if I don't reboot system. When it happens I try to restart my network manager with: ```
sudo service network-manager restart
``` and enable my wireless card with ```
sudo ip link set 'interface name' up
``` but not only my device remains off, it results as "not ready". Furthermore the terminal gives me the error ```
RTNETLINK answers: input/output error
```If I remember correctly, months ago I had the same issue always with an Ubuntu-based distro, then I installed some other distros and I don't remember If them gave me the same trouble.

---

### Post by jeremy31 on 2017-09-09
See the wireless script link in my signature and post results

---

### Post by chief096 on 2017-09-09
If I have done all correctly, this is the output:

---

### Post by jeremy31 on 2017-09-09
Try this and reboot ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
This disables Network Manager from enabling wireless power management.  Power management is usually responsible for disconnects

---

### Post by chief096 on 2017-09-09
Ok, I'll try it now. I leave the thread as "unresolved" for a few days for make sure that your solution works.

---

