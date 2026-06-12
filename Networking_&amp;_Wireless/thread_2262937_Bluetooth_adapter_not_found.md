---
title: "Bluetooth adapter not found"
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by sarower2 on 2015-01-28
Hi
i am a new user of ubuntu 14.04 in [COLOR=#008000]HP pavilion g4[/COLOR]
in system setting --->bluetooth menu ---> show [COLOR=#008000]no adapter found. [/COLOR]
what can i do now ?? plz help me

---

### Post by jeremy31 on 2015-01-28
Solved?

---

### Post by sarower2 on 2015-01-31
plz help me

---

### Post by jeremy31 on 2015-01-31
> **sarower2 said:**
> plz help me

Post the results from terminal for ```
lspci -nnk | grep -iA2 net
``````
lsusb
```

---

### Post by sarower2 on 2015-02-01
> **jeremy31 said:**
> Post the results from terminal for ```
lspci -nnk | grep -iA2 net
``````
lsusb
```

sarower@sarower-HP-Pavilion-g4-Notebook-PC:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183b]
    Kernel driver in use: r8169
sarower@sarower-HP-Pavilion-g4-Notebook-PC:~$ lsusb
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2015-02-01
That one might never work as the manufacturer isn't willing to support it in Linux for some reason

Plenty of bug reports [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721)
[https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1355096](https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1355096)

---

