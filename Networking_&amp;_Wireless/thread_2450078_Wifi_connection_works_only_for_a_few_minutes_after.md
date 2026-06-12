---
title: "Wifi connection works only for a few minutes after reboot"
date: 2020-09-07
forum: Networking &amp; Wireless
---

### Post by zakey2 on 2020-09-07
I just installed ubuntu and I'm having a problem connecting to the internet, so basically after booting the system the wifi connection work totally fine but after a minute or so a question mark appears on the wifi icon and I lose the internet connection  (it still works fine on other devices) and when I try to connect to different wifi network it gives me an error "connection failed activation of network connection failed" if I turn off the wifi and turn it back on the question mark disappears and I can see the signal bars but there's no internet connection still.
Btw I'm using a fairly old laptop.

---

### Post by kc1di on 2020-09-07
We need to know a bit more about your system.  IE wireless card.  
If you are not sure go to a terminal and enter this command and post the output here. ```
lspci
```

---

### Post by zakey2 on 2020-09-07
The card is a ralink Corp. RT5390 wireless 802.11n

---

### Post by zakey2 on 2020-09-07
The problem appears to be power management, this fixed it for me:
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

---

### Post by jeremy31 on 2020-09-07
Please use the thread tools menu at the top right of the page to mark as solved.  Also consider filing a bug report, see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) so we might be able to get this to be the default state again

This was caused by this bug report [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1557026](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1557026)

---

