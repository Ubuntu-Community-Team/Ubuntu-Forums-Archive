---
title: "Ubuntu 16.04 LTS with intel wireless 8260 - wifi does not work"
date: 2018-02-10
forum: Networking &amp; Wireless
---

### Post by charlotte20 on 2018-02-10
Hello everyone, I have an HP ZBook Studio G3 and i just installed ubuntu 16.04 (i am completely new to ubuntu) but i cant get the wifi to work.

I already found out that my network controller is an intel wireless 8260 and i found out that there were more people having problems with this but i havent found the right solution yet.

I tried installing iwlwifi-8000C-13.ucode but im not sure if it worked, it didnt give an error message but after rebooting my wifi still didnt work.

Please help me!

---

### Post by jeremy31 on 2018-02-10
*Thread moved to **Networking & Wireless**.*
Please see the wireless script link in my signature and post results

---

### Post by chili555 on 2018-02-10
Please run and post:```
lspci -nnk | grep 0280
sudo modprobe iwlwifi && dmesg | grep iwl
rfkill list all
```

---

