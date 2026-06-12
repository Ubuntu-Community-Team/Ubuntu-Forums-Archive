---
title: "Wifi not working on HP 15 BS180TX"
date: 2018-07-05
forum: Networking &amp; Wireless
---

### Post by adityapc on 2018-07-05
[B][COLOR=#008080]aditya@AdityaPC:~$ lspci -v | grep -i network
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723


[/COLOR]This is the network controller. I tried a lot of methods mentioned on ubuntu forum but issue is still there.
I have Ubuntu 18.04 LTS dual boot with Windows 10 Pro.
Wifi works perfectly on Windows.
Wifi not working on ubuntu. Please help. (I have the latest kernel installed.)[/B]

---

### Post by wildmanne39 on 2018-07-05
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by jeremy31 on 2018-07-05
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
cd /lib/firmware/rtlwifi
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/rtlwifi/rtl8723defw.bin
```
Reboot

---

