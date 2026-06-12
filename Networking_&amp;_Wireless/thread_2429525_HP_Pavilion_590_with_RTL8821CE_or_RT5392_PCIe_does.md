---
title: "HP Pavilion 590 with RTL8821CE or RT5392 PCIe doesn't see WiFi"
date: 2019-10-19
forum: Networking &amp; Wireless
---

### Post by tormec on 2019-10-19
Hi,
Recently I've bought an [HP Pavilion 590-p0008nl]("https://support.hp.com/us-en/document/c06069529") at which I've mounted a [NILOX wireless PCI express card]("ftp://ftp.nilox.com/Manuali/16NXPE01CQ001-16NXPE0130001(QSG_IES).pdf") [1] because I wasn't able to see my WiFi Network.

I'm using Ubuntu 18.04 with kernel 5.0.0-31-generic and this is the list of my network hardware:
```
sudo lshw -C network

 *-network                 
       description: Wireless interface
       product: RT5392 PCIe Wireless Network Adapter
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 00
       serial: 78:44:76:c0:2b:b5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=5.0.0-31-generic firmware=0.40 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:57 memory:fe600000-fe60ffff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:17:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:fe300000-fe30ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:1c:00.0
       logical name: enp28s0
       version: 15
       serial: c4:65:16:14:38:c7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:d000(size=256) memory:fe504000-fe504fff memory:fe500000-fe503fff
```

I've tried to install the driver for RTL8821CE following the instructions described at [https://github.com/tomaspinho/rtl8821ce](https://github.com/tomaspinho/rtl8821ce) and even disabling the SecureBoot I can't use my WiFi [2]. I think that procedure doesn't work properly with kernel 5.*.

Why I can't use my wireless PCI card? Do you think there is any kind of conflict between drivers?


[1] I used this PCI card with my previous PC under Ubuntu 16.04.
[2] The WiFi is seen only for a couple of seconds as soon as I turn on the PC.


Thanks.

---

### Post by praseodym on 2019-10-20
[https://github.com/tomaspinho/rtl8821ce/tree/v5.5.2](https://github.com/tomaspinho/rtl8821ce/tree/v5.5.2)

This branch seems newer

---

### Post by tormec on 2019-10-21
Installing the driver RTL8821ce from that branch doesn't solve the problem.

I'm still wondering why an external PCI card is not completely recognised?
Do you think the problem is just its driver, the RT5392? Maybe I'll try the step *How to update the driver after a Linux kernel upgrade* reported at [https://github.com/agerwick/RT28XX-RT539X-Linux-driver](https://github.com/agerwick/RT28XX-RT539X-Linux-driver)

---

### Post by tormec on 2019-10-26
At the end I've been able to install the driver for RTL8821CE following [https://github.com/shubham151/rtl8821ce](https://github.com/shubham151/rtl8821ce)

```

git clone https://github.com/shubham151/rtl8821ce.git
cd rtl8821ce
sudo make all
sudo make install

```
Then it's neccessary to save the name of the module in /etc/modules. Finally restart.

---

### Post by tormec on 2020-03-14
Since every now and then I still had some issues with the internet connection, Today I've decided to move from ubuntu 18.04.1 to 18.04.4 and to install [https://packages.ubuntu.com/bionic-updates/rtl8821ce-dkms](https://packages.ubuntu.com/bionic-updates/rtl8821ce-dkms), which can be found in Synaptic. The wifi has been recognized immediately!!

---

