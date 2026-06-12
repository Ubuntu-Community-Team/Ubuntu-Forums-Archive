---
title: "Atheros WLAN Bitrate is always limited 1Mb/s"
date: 2017-05-30
forum: Networking &amp; Wireless
---

### Post by e.benkler on 2017-05-30
On Ubuntu zesty, I have only 1Mbit/s WLAN bitrate, although the router supports (and with other devices actually delivers) >54Mbit/s. The router is a FritzBox 7360 SL with up to date FritzOS 06.33. The WLAN driver is ath10k_pci, in an Acer F5-771G-70P8 laptop. Of course, I have been searching this forum and googling, but there seems to exist a large manifold of different issues that can lead to this symptom, so I did not find a solution yet. I tried to disable power management for the WLAN adapter, without success. The bitrate is also limited to 1Mb/s during downloads, so it doesn't seem to be a reduced rate for power saving purposes.
 
Results of the wireless-info script: [http://paste.ubuntu.com/24718207/](http://paste.ubuntu.com/24718207/)

Can somebody give me a hint what I could try to achieve higher WLAN bitrate? Thanks in advance for the help.

---

### Post by jeremy31 on 2017-05-30
I would check that info against a speedtest.com and disable Network Manager from trying to enable wifi power management with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

