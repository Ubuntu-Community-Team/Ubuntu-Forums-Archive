---
title: "No WiFi adapter found in Ubuntu 18.04,3 for hp Pavilion 14-ce0009nf"
date: 2019-08-16
forum: Networking &amp; Wireless
---

### Post by naram22 on 2019-08-16
Hello all,

I installed ubuntu 18.04.3 yesterday on dual boot with windows 10 yesterday, and since then I've been trying to solve this issue of Wifi adapter, 

I followed the solution of this post : [https://ubuntuforums.org/showthread.php?t=2392454&page=3](https://ubuntuforums.org/showthread.php?t=2392454&page=3), but it doesn't work for me.

Here are some information on my system :

```
##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic

##### kernel ############################

Linux 5.0.0-25-generic #26~18.04.1-Ubuntu SMP Thu Aug 1 13:51:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
        Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
        Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84b9]
        Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:b00a Realtek Semiconductor Corp.
Bus 001 Device 002: ID 04f2:b627 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

Thank you for your help.

---

### Post by chili555 on 2019-08-16
Please see: [https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258](https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258)

Please note that you hace the same 10ec:c821 device.

---

### Post by naram22 on 2019-08-16
Thank you very much. The wifi works now ;)

---

