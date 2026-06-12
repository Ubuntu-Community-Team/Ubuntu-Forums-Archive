---
title: "Wi-Fi setting keeps disappearing"
date: 2021-12-20
forum: Networking &amp; Wireless
---

### Post by tahitiwibble on 2021-12-20
My modem/router works perfectly with my Windows laptop but I've just started using Ubuntu again on a daily basis and the Wi-Fi setting in "Settings" just disappears and I disconnect from the net. This happens a few times a day and I have to reboot to be able to reconnect.

Any kind soul out there have an idea how to at least kick start the wi-fi without rebooting?

---

### Post by praseodym on 2021-12-21
Please run the wireless script from the sticky thread and show the outputs

---

### Post by tahitiwibble on 2021-12-21
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs

Thank you praseodym for your help! Hopefully the txt file will be attached to this reply as wished for. :-s

[ATTACH]289654[/ATTACH]

---

### Post by praseodym on 2021-12-22
Lets try the classic approach:

```
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```
Do also change encryption in your router to WPA2-AES only, no mixed mode

---

### Post by tahitiwibble on 2022-01-12
> **praseodym said:**
> Lets try the classic approach:

```
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```
Do also change encryption in your router to WPA2-AES only, no mixed mode

Please forgive my absence of late. It's been a harrowing transition from 2021 to 2022.

I have only just today come back to your response and have followed all instructions to the letter. Thank you once again for your help! I will let you know how the "classic approach" unravelled.

---

