---
title: "WiFi losing signal, Network controller: Intel Corporation Dual Band Wireless-AC 3165"
date: 2020-01-10
forum: Networking &amp; Wireless
---

### Post by agnieszka2 on 2020-01-10
The problem appears on freshly installed Ubuntu 18.04 on Lenovo IdeaPad (originally it came with Windows). Wifi seems to be turned on all the time but from time to time (sometimes it works fine for a few days, more often it happens every few hours, sometimes a few times in one hour) it looks like loosing signal - it begins to be weaker and weaker to breaking up completely. Sometimes turning wifi off and on helps, sometimes even restart doesn't. Everything is back to normal after 20-30 minutes, sometimes sooner, sometimes later. Wifi itself and router work fine as we've got no problems with other devices at all. 

The output of `lspci | grep -i "Wireless\|Wifi"` is `01:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth (rev 99)`

Could you please help?

---

### Post by praseodym on 2020-01-12
Please try
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by agnieszka2 on 2020-01-13
The results are respectively:

options iwlwifi 11n_disable=1

remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod mac80211
rmmod cfg80211


insmod /lib/modules/5.0.0-37-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/5.0.0-37-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko 11n_disable=1 

Could you please explain what do these do?

---

### Post by praseodym on 2020-01-13
It disables the N-mode, a typical Intel feature. Did it improve stability? If not do
```

sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by agnieszka2 on 2020-01-17
Sorry for the delay. It looks like it helped. Thank you for your support!

---

