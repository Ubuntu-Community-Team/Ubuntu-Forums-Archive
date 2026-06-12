---
title: "Ubuntu 16.04 Lenovo L570 wifi driver"
date: 2018-03-19
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2018-03-19
I have an Lenovo Thinkpad L570 where i would like to be able to connect to wifi.

So far i have installed the network-manager package that contains the tools like nmcli and added
```

auto wlan0
iface wlan0 inet dhcp

```
to /etc/network/interfaces

When i look at my network devices sudo lshw -C network i get the following output
> 
*-**network UNCLAIMED**     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:f2600000-f2601fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (4) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: 98:29:a6:7f:10:85
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.1-4 ip=192.168.1.220 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:129 memory:f2700000-f271ffff


Does unclaimed mean that Ubuntu does not recognize the device and a firmware install / upgrade is needed?

Thanks on advance
Best regards

---

### Post by jeremy31 on 2018-03-19
Please post results for ```
lspci -nnk | grep -iA3 net; uname -a
```
Unclaimed means no driver for it, sometimes we can modify the source code to make it work

---

### Post by Drenriza on 2018-03-19
output of those command are
> 
$ lspci -nnk | grep -iA3 net; uname -a
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-V [8086:15d8] (rev 21)
    Subsystem: Lenovo Ethernet Connection (4) I219-V [17aa:2249]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
03:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:1010]
04:00.0 Non-Volatile memory controller [0108]: Intel Corporation Device [8086:f1a5] (rev 03)
    Subsystem: Intel Corporation Device [8086:390a]
Linux lt01 4.4.0-87-generic #110-Ubuntu SMP Tue Jul 18 12:55:35 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


---

### Post by jeremy31 on 2018-03-19
I think the 4.13 kernel supports that ```
sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04
```
Should work according to [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop)

---

### Post by Drenriza on 2018-03-19
That worked in the sense that the wifi device was found / claimed? and i was able to establish a wireless connection and browse the web.

Thank you!
On a side note, what does
```

apt-get install --install-recommends

```
do?

I noticed in packages that would be installed, that their was also packages for some VMware and Radeon stuff?

---

