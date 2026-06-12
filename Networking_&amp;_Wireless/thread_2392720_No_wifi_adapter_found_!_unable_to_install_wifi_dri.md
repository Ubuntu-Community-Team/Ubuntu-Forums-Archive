---
title: "No wifi adapter found ! unable to install wifi driver( rtl8723be) !!"
date: 2018-05-24
forum: Networking &amp; Wireless
---

### Post by xplatypus07 on 2018-05-24
The wifi doesn't show up, Bluetooth is automatically turned on and airplane mode turns on when bluetooth is switched off !
Secure boot is disabled ! currently is am using Ubuntu 18.04 bionic . My network adaptor is 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:81ec]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]
    Kernel modules: rtl8723be
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

ANYONE HELP ME ! 

Thank You !

---

### Post by kc1di on 2018-05-24
could you go to a terminal and type ```
rfkill list
``` and post the results here.
also install inxi with this command```
sudo apt install inxi
```
When that finishes issue this command ```
inxi -Fxz
``` post the results.
This [Ask ubuntu post]("https://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work") may also be helpful

---

### Post by xplatypus07 on 2018-05-24
These are the results for your commands

Also i tried the steps from [https://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work](https://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work) link but notihng happended ..

---

### Post by kc1di on 2018-05-25
[This page ]("https://akshaycv006.wordpress.com/2017/01/12/installing-realtek-rtl8723be-driver-for-ubuntu-debian-or-fedora/")may be of help - good luck.

---

### Post by praseodym on 2018-05-25
Deactivated SecureBoot?

---

