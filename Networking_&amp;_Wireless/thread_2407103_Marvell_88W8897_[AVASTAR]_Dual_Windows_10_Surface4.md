---
title: "Marvell 88W8897 [AVASTAR] Dual Windows 10 Surface4 Wifi Drops"
date: 2018-11-29
forum: Networking &amp; Wireless
---

### Post by aeisner on 2018-11-29
I have issues with network-manager. I've dual booted Ubuntu 18.04 on a Surface Pro 4 with Windows 10. I can connect to a wireless network but the connection drops after various times: minutes to hours. What's more, when it does drop and I reboot the machine, network manager slows down the shutdown time. I've ran an update and dist-upgrade already. Attached is the wireless-info results.

[ATTACH]281822[/ATTACH]

---

### Post by praseodym on 2018-11-30
Try Wicd instead

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
```
Deactivate Networkmanager from Autostart and add wicd instead using 

```
wicd-client --tray
```
as command (if not already there) and re-login

---

