---
title: "HP BS545tu rtl8723d  wifi issue"
date: 2018-05-26
forum: Networking &amp; Wireless
---

### Post by git786 on 2018-05-26
wifi  not  detected  in  ubuntu  18.4  kernel version  15.20

---

### Post by jeremy31 on 2018-05-26
Welcome to the forums, in terminal do
```
sudo apt update && sudo apt install git dkms build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```
Reboot

---

