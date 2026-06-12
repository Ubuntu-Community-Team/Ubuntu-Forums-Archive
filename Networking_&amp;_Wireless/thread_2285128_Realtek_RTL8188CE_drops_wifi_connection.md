---
title: "Realtek RTL8188CE drops wifi connection"
date: 2015-07-03
forum: Networking &amp; Wireless
---

### Post by fourbit2 on 2015-07-03
Ok, I have looked and looked and tried and tried a lot of things about this. And, nothing. I think I'm more confused that ever. 

Anyhow, my wifi keeps closing after a short time. To bring it back, I click on the dropdown to disable the wifi and then click it again to enable. The network doesn't even show in the list when it drops out. But, returns when I disable/enable the wireless. 

Anyhow, here is my wifi-info.txt. (I think) :(

---

### Post by praseodym on 2015-07-04
Try these module parameter

```
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot

---

### Post by Pilot6 on 2015-07-04
What did you try? Did you install a driver from github or ppa:hanipouspilot/rtlwifi

?

---

