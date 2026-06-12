---
title: "no wifi adapter in ubuntu 18.05"
date: 2018-07-17
forum: Networking &amp; Wireless
---

### Post by fakincantauria on 2018-07-17
Hi, yesterday I installed Ubuntu 18.05 in dual boot with Windows 10 but it doesn't recognize mi wifi card (In windows I have no problem). I've tried reinstalling and other things but it's the same. Can you help me plzzzzzzz. I am semi noob in this, and here's is the wireless information script that I read in another post that it's important: [http://paste.ubuntu.com/p/Hhv5PtRG6X/](http://paste.ubuntu.com/p/Hhv5PtRG6X/). 

Thanks! :D

---

### Post by jeremy31 on 2018-07-17
I would try
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
cd rtlwifi_new
make 
sudo make install
```
Reboot

---

### Post by fakincantauria on 2018-07-17
WOOOOOOOOOOW that works. You're awesome, many many many thanks :P

---

