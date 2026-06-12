---
title: "ehternet &amp; Wifi device isn't working in my laptop"
date: 2015-08-21
forum: Networking &amp; Wireless
---

### Post by swopnil on 2015-08-21
Hi,
I am new user in ubuntu 14.04 LTD. HP Probook 450 G1 is my laptop. When I install ubuntu here is not working ethernet & wifi device. How I solve this problem ?

---

### Post by Bucky Ball on 2015-08-21
You could start by providing us with the output from this command:

```
sudo lshw -C network
```

... between code tags (see the last link in my signature for how) or by posting the output of the wireless script in my signature to help us help you. We can't do a lot with the information provided so far. :)

PS: Try ethernet or wireless, not both. If ethernet is plugged in it will generally preclude wireless from responding.

---

### Post by swopnil on 2015-08-22
When I command sudo lshw -C network
then show this code

```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 0c
       serial: a0:1d:48:aa:7e:e4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:3000(size=256) memory:b0700000-b0700fff memory:b0400000-b0403fff
  *-network UNCLAIMED
       description: Network controller
       product: MT7630e 802.11bgn Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b0600000-b06fffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@3:2
       logical name: wlan0
       serial: 00:1f:1f:6b:34:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.13.0-62-generic firmware=0.29 ip=192.168.0.102 link=yes multicast=yes wireless=IEEE 802.11bgn
```


but, how can i install wifi drive ?

---

### Post by Bucky Ball on 2015-08-22
> **swopnil said:**
> but, how can i install wifi drive ?

Why do you think I asked for the output (and also asked for it between code tags, thanks ... see the last link in my signature, I have added them to your last post)? How can we tell you how to install the wifi driver if we have no idea what it is or what driver it is using presently? :) 

See [HERE]("http://community.linuxmint.com/tutorial/view/1796") and [HERE]("https://duckduckgo.com/?q=MT7630e+ubuntu").

You have this wireless chip:

```
product: MT7630e 802.11bgn Wireless Network Adapter
vendor: MEDIATEK Corp.
```

... using this driver:

```
driver=rt2800usb driverversion=3.13.0-62-generic
```

Don't think that's the correct one.

---

