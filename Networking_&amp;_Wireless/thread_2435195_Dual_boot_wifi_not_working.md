---
title: "Dual boot wifi not working"
date: 2020-01-17
forum: Networking &amp; Wireless
---

### Post by coletonspeer on 2020-01-17
Hi, I have a dual boot of ubuntu on my pc and I am having some wifi issues. I have checked multiple threads and have not found a working answer. so the wifi did not work when I initially installed ubuntu but then one day it just worked I updated the pc yesterday and it just stopped working again. it is a USB wifi adapter. [ATTACH]284815[/ATTACH]

---

### Post by jeremy31 on 2020-01-17
Remove the auto wlan from /etc/network/interfaces
Then do ```
sudo apt install git dkms
git clone github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
```
Reboot

---

