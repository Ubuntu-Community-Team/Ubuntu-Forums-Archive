---
title: "TL-WN722N stopped working at ubuntu 16.04"
date: 2017-11-06
forum: Networking &amp; Wireless
---

### Post by blackbunny13 on 2017-11-06
I have used following steps. It would work properly. But suddenly the TL-WN722N is not working on my ubuntu 16.04.



sudo apt-get install git dkms
cd /usr/src
sudo git clone [https://github.com/lwfinger/rtl8188eu.git](https://github.com/lwfinger/rtl8188eu.git)
sudo dkms add ./rtl8188eu
sudo dkms build 8188eu/1.0
sudo dkms install 8188eu/1.0
sudo modprobe 8188eu

---

### Post by jeremy31 on 2017-11-06
See the wireless script link in my signature and post results

---

