---
title: "Wi-fi randomly stops. Supplicant network-manager issues. Failed to set WFD IES and re"
date: 2019-07-23
forum: Networking &amp; Wireless
---

### Post by ngeooz on 2019-07-23
I've been having this issue for weeks. I looked it up in the web but doesn't seem to be working solutions.

The thing is that after a couple of hours of use my wifi randomly disconnects.

While the network is working, if I do 

```
    sudo service network-manager status
```
There's no issue at all.
The device (wlo1) activation is "successful, device activated". and the supplicant is okay, saying "supplicant: wpa_supplicant die count reset".

Meanwhile, if I check the network manager status when is down. I've two warns.

The status explain in one hand

```
    supplicant: failed to set WFD IEs on wpa_supplicant: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconneected from message bus without replying
```

And, in the other hand

```
    device (wlo1): re-acquiring supplicant interface (#1)
```

Any help really would help. Thanks.


Details of my wireless card:

```
    *-network                 
           description: Ethernet interface
           product: RTL810xE PCI Express Fast Ethernet controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:01:00.0
           logical name: eno1
           version: 07
           serial: b0:5a:da:d0:bb:31
           size: 10Mbit/s
           capacity: 100Mbit/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
           resources: irq:16 ioport:2000(size=256) memory:91004000-91004fff memory:91000000-91003fff memory:91500000-9150ffff
      *-network
           description: Wireless interface
           product: RTL8188EE Wireless Network Adapter
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:02:00.0
           logical name: wlo1
           version: 01
           serial: 18:4f:32:b6:95:3a
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=rtl8188ee driverversion=5.0.0-20-generic firmware=N/A ip=192.168.0.110 latency=0 link=yes multicast=yes wireless=IEEE 802.11
           resources: irq:121 ioport:1000(size=256) memory:91100000-91103fff

```

Edit: I use Ubuntu 19.04 Disco Dingo.

---

### Post by ngeooz on 2019-08-01
I'm commenting to highlight the question and follow up the answers.

---

### Post by midoelhawy on 2019-10-02
I have the same **problem**

---

