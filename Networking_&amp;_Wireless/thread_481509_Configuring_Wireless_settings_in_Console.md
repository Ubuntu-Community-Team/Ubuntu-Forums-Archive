---
title: "Configuring Wireless settings in Console"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by finaldata on 2007-06-22
Hi,

Need help on what programs or files are to be edited so that i could configure my wireless settings in console. I can't seem to login to gui because of ati driver problems... right now i'm just sorting out how to configure my wireless settings... where do i set up the SSID? what files do i edit or run to edit that? All the help will be highly appreciated.

Thanks...

---

### Post by Kobalt on 2007-06-22
If you want to do that, you might want not to use Network-Manager, meaning that if you use Ubuntu 7.04 you should uninstall it first. Then you should edit this file ```
sudo nano /etc/network/interfaces
```
At your wireless interface section (I'll assume it's wlan0, but change it to suit yours), enter your SSID and encryption key this way : > iface inet wlan0 dhcp
wireless-essid XXXXXXX
wireless-key XXXXXX
This is for a very standard dhcp wifi connection. If you use other settings, come back here with surther details. 
Then launch your connection this way ```
sudo ifdown wlan0
sudo ifup wlan0
```

---

