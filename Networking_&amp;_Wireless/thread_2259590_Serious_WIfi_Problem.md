---
title: "Serious WIfi Problem"
date: 2015-01-05
forum: Networking &amp; Wireless
---

### Post by extraacc420 on 2015-01-05
I am in deep trouble with my dell laptop using ubuntu 12.04. I have tried in many ways but failed.

root@Prince:/home/prince# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 07
       serial: b8:2a:72:9b:49:68
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
If anyone please suggest me some solutuon of my problem. Advance thanx to all.

---

### Post by praseodym on 2015-01-05
Which kernel is in use? Does LAN work?
```

uname -a
```

---

### Post by jeremy31 on 2015-01-05
Unless there is some reason you can't use 14.04, I would switch

---

### Post by extraacc420 on 2015-01-05
I am already working with wired internet connection. But unfortunately wifi is not working. It tells me that wireless is disable by hardwire switch in networking section.

root@Prince:/home/prince# uname -a
Linux Prince 3.2.0-74-generic #109-Ubuntu SMP Tue Dec 9 16:45:49 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by praseodym on 2015-01-05
Please check updating the kernel:
```

sudo apt-get -s install --install-recommends linux-generic-lts-trusty linux-image-generic-lts-trusty linux-headers-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty build-essential dkms
``` 
This is just a test. If it works without errors, repeat it without "-s".

---

