---
title: "Wifi and Bluetooth are not working after installation of ubuntu 18.04"
date: 2018-09-24
forum: Networking &amp; Wireless
---

### Post by akta on 2018-09-24
I have dell vostro 3446 version in laptop machine. I have now installed  ubuntu 18.04 version. After that bluetooth and wifi has been stopped  working. Even camera also stopped working. I think it has some missing drivers. Before than that I had ubuntu 16 LTS version, both bluetooth,wifi was  working fine. Please suggest some better and easy solution for the same.

$ lspci -nnk | grep -iA3 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0662]
    Kernel driver in use: r8168
    Kernel modules: r8168
08:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)

$ lsusb
Bus 001 Device 003: ID 064e:9205 Suyin Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 2717:ff80  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lsmod | grep cfg

$ uname -r
4.15.0-34-generic

---

### Post by jeremy31 on 2018-09-24
I would check in BIOS to see if WLAN and Bluetooth are enabled and possibly reset BIOS to defaults if no WLAN/Bluetooth options are found

---

### Post by akta on 2018-09-26
Both are enabled

---

### Post by jeremy31 on 2018-09-26
Can you download a 16.04 ISO and see if wifi still works in it?

---

### Post by akta on 2018-09-26
ya it is working fine till just before i have upgraded to 18.04 from 16.04 LTS, I think there is missing driver for wifi in that case if you can help then it will better.

---

### Post by jeremy31 on 2018-09-27
But the wifi device is not being shown by lspci like someone has removed it from the machine

---

