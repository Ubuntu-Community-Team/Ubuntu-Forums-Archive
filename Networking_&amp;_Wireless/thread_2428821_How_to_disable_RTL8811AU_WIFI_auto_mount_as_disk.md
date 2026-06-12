---
title: "How to disable RTL8811AU WIFI auto mount as disk?"
date: 2019-10-09
forum: Networking &amp; Wireless
---

### Post by pazystamas2 on 2019-10-09
Hello,
How to disable RTL8811AU USB WiFi adapter auto mount? After boot, nautilus auto mounts WiFi as USB disk (with windows drivers) and wifi only works after unmounting disk. I don't want to disable all others flash disk mounting, only this WiFi adapter. Ubuntu 19.04 
Installed with:
```

[COLOR=#000000][FONT=&amp]sudo apt update
[/FONT][/COLOR]sudo apt install build-essential git dkms
git clone https://github.com/brektrou/rtl8821CU.git
cd rtl8821CU
chmod +x dkms-install.sh
sudo ./dkms-install.sh 
sudo modprobe 8821cu
```
Bus 003 Device 006: ID 0bda:c811 Realtek Semiconductor Corp.
sudo dpkg -s usb-modeswitch | grep Status
Status: install ok installed

---

### Post by jeremy31 on 2019-10-10
What is the USB ID before unmounting?

---

### Post by pazystamas2 on 2019-10-11
> **jeremy31 said:**
> What is the USB ID before unmounting?
Mounted as USB disk Bus 003 Device 005: ID 0bda:1a2b Realtek Semiconductor Corp. 
Mounted as WIFI adapter Bus 003 Device 006: ID 0bda:c811 Realtek Semiconductor Corp.
Using this 4 Euro adapter: [https://www.aliexpress.com/item/32961658192.html?spm=a2g0s.9042311.0.0.27424c4dkrPrSi](https://www.aliexpress.com/item/32961658192.html?spm=a2g0s.9042311.0.0.27424c4dkrPrSi)

---

### Post by jeremy31 on 2019-10-11
See [https://askubuntu.com/a/1082418/300665](https://askubuntu.com/a/1082418/300665)

---

### Post by pazystamas2 on 2019-10-12
Thanks, it worked!

---

