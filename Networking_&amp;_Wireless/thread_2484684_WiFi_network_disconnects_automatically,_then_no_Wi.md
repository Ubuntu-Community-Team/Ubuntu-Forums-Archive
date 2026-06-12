---
title: "WiFi network disconnects automatically, then no WiFi networks are visible"
date: 2023-03-06
forum: Networking &amp; Wireless
---

### Post by grugel on 2023-03-06
I am a novice on Ubuntu 22.04. My laptop connects to WiFi networks fine, but after some time it disconnects automatically. Then no WiFi networks are visible in the scanning list. After restarting the laptop it connects to WiFi networks fine, again after some time it disconnects automatically. Then again no WiFi networks are visible in the scanning list. Note that, all the programs are up to date, so no additional drivers are available.


Here are the logs:


rtw_8822be failed to read ASPM
rtw_8822be failed to power on mac
rtw_8822be failed to poll offset=0x5 mask=0x2 value=0x0


Laptop model: Lenovo Ideapad S340-14IWL
WiFi adapter: Realtek RTL8822BE


How to fix this problem?

---

### Post by jeremy31 on 2023-03-06
Try disabling wifi power management with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by grugel on 2023-03-13
I tried disabling wifi power management, then rebooted the laptop. But nothing worked. Now the update is my laptop connects to wifi networks normally, but there is no internet access. Can you suggest me another solution?

---

