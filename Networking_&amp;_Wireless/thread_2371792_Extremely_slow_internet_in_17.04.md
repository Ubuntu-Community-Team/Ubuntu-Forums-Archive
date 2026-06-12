---
title: "Extremely slow internet in 17.04"
date: 2017-09-18
forum: Networking &amp; Wireless
---

### Post by gaurav_kumar3 on 2017-09-18
Hi
 I recently installed ubuntu and it's giving very slow speeds (max 30 kbps) in connecting to my mobile hotspot (which on windows 10 and on mobile gives download speed upto 600-700 kbps).

I ran this script ([https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)) and got this output ([http://paste.ubuntu.com/25569756/](http://paste.ubuntu.com/25569756/))

Can anyone please help? Thanks in advance.

---

### Post by wildmanne39 on 2017-09-19
Please do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
Go into network manager settings and set your network settings to match the screenshots:
Then do:
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot

---

