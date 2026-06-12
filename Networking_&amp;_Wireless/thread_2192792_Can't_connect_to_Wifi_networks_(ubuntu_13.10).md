---
title: "Can't connect to Wifi networks (ubuntu 13.10)"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by russell_devine on 2013-12-09
This week I purchased a [new laptop]("http://h20386.www2.hp.com/AustraliaStore/Product.aspx?pdetail=P305368&") (follow link for specs) in which I replaced the HD with an SSD and installed a fresh ubuntu 13.10 system onto, following which I ran the updater to ensure the latest software and patches were installed.

At no time with the laptop have I had any success with connecting to the wireless network at home. I have an Acer laptop at home running ubuntu 13.04 which is facing no issues at all connecting the wireless network along with the Mac and three Windows laptops my house contains. When I attempt to connect to the wireless, after reboot it will connect for a second then immediately disconnect, when I delete it from the Network Connections to rediscover it and enter in the password again it will disconnected after a millisecond of connection. I have fiddled allot with the Network Connections trying to re-enter the password and so fourth but to no success. Connecting via an Ethernet cable is fine which is how I managed to update my laptop with the latest patches.

As my ubuntu knowlegde is relatively in its infancy I am unsure whether there is any information I can add to assist with this issue... I really would like to use ubuntu on the new laptop but if connecting to wireless networks is going to be an issue then it's pretty unrealistic to continue to do so, yet I want to learn more about linux :(

---

### Post by codenine75a on 2013-12-09
I hope you are not working around a Jacob's ladder because the static charge would probably affect your wifi connection.  I would look at your signal strength.

---

### Post by Bucky Ball on 2013-12-09
Welcome. Please provide the output of this command:

```
sudo lshw -C network
```

@codenine75a:

> **codenine75a said:**
> I hope you are not working around a Jacob's ladder because the static charge would probably affect your wifi connection.  I would look at your signal strength.

Please read posts carefully. OP states they are having no issues whatever with wireless on four other machines.

---

### Post by russell_devine on 2013-12-10
> **Bucky Ball said:**
> Welcome. Please provide the output of this command:

```
sudo lshw -C network
```

Here is output:

```
  *-network       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 34:23:87:2d:9c:6b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.11.0-14-generic firmware=0.37 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 memory:b2610000-b261ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 0c
       serial: a0:1d:48:6f:2e:27
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:b2500000-b2500fff memory:b2400000-b2403fff
```

---

