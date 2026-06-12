---
title: "hp envy 15t-ae100 cannot see wifi"
date: 2019-05-18
forum: Networking &amp; Wireless
---

### Post by zero22 on 2019-05-18
[COLOR=#242729][FONT=Arial]I have tried tons of codes from the internet with many different versions of Ubuntu but none of the tries shows up the wifi list successfully. I'm running Ubuntu on virtualbox but it only connects to Ethernet and it's working but I want to use wifi no the Ethernet. What's the official way to do it? I have tried most of the things on the internet so please help me different way. Thank you[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I will keep typing here what I have tried: //if i go to settings -> wifi -> no wi-fi adapter found// //sudo apt-get install linux-headers-$(uname -r) build-essential git// //git clone [https://github.com/lwfinger/rtlwifi_new.git//](https://github.com/lwfinger/rtlwifi_new.git//) //cd rtlwifi_new/ && git checkout origin/extended -b extended// //sudo make install//[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]//sudo modprobe -r rtl8723de <- showed nothing// //sudo modprobe rtl8723de <- showed nothing//[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]////////////////////////////////////////////////////////////// lspci -nnk | grep -iA3 net; mokutil --sb-state 00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02) Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e] Kernel driver in use: e1000[/FONT][/COLOR]
**Kernel modules: e1000**

[COLOR=#242729][FONT=Arial]00:08.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02) Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e] Kernel driver in use: e1000 Kernel modules: e1000 00:09.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02) Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e] Kernel driver in use: e1000 Kernel modules: e1000 00:0a.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02) Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e] Kernel driver in use: e1000 Kernel modules: e1000 EFI variables are not supported on this system[/FONT][/COLOR]

---

### Post by praseodym on 2019-05-19
Please use code tags and show
```

lspci -nnk
lsusb
```

---

### Post by jeremy31 on 2019-05-19
Is Ubuntu the guest OS?  If so you will likely need a USB wifi adapter if you want to control what AP the wifi connects to in Ubuntu
Virtualbox normally makes a virtual bridge from the host OS to a virtual ethernet device on the guest

---

