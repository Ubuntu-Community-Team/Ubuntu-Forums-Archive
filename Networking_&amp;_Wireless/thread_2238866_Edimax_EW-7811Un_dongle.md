---
title: "Edimax EW-7811Un dongle"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by Zenoxio on 2014-08-10
[COLOR=#333333][FONT=UbuntuRegular]I have this WiFI dongle:[http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/wireless_adapters_n150/ew-7811un](http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/wireless_adapters_n150/ew-7811un)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Is there an Ubuntu package I can use to get it working? If not, how can I get this WiFi to work? I'm running a CLI, no GUI. Running v14.04
[/FONT][/COLOR]

---

### Post by praseodym on 2014-08-10
Does LAN work? If yes change the driver via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by Zenoxio on 2014-08-10
Thanks! No errors doing that, what after that? I have a WPA network, but I don't see WPA documentation listed in iwconfig

EDIT: I'm trying wpa_supplicant, but it's telling me "Driver does not support authentication/association or connect commands"

---

