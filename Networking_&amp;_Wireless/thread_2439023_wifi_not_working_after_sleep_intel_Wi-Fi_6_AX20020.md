---
title: "wifi not working after sleep intel Wi-Fi 6 AX200/201"
date: 2020-03-21
forum: Networking &amp; Wireless
---

### Post by freak-on on 2020-03-21
Hello, 
running on HP Laptop 15t-dy100 

( sorry about my English it's not my first lang) 

every time my laptop goes to sleep my wifi is disabled and airplane mode is on and cannot switch off.

went through the "before posting" Thread and uploaded my wireless info [https://pastebin.com/raw/RvdC6EHu](https://pastebin.com/raw/RvdC6EHu)

note `rfkill` shows a hard block on the device.

just after I reboot the wifi is functional.

thanks in advance for all contributors.

---

### Post by freak-on on 2020-03-22
does anybody have an idea where is the problem?:confused:

---

### Post by jeremy31 on 2020-03-24
See if disabling wifi power management fixes it ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

