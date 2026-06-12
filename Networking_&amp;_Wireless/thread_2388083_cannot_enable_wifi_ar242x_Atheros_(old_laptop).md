---
title: "cannot enable wifi ar242x Atheros (old laptop)"
date: 2018-03-28
forum: Networking &amp; Wireless
---

### Post by matrooswolf on 2018-03-28
Hi,

I reinstalled an old laptop with ubuntu17.10, but wifi is not working. I cannot enable it.

The wifi device is an Atheros ar242x. It used to work well under the old install, which was till ubuntu 14.04, I think... But now i'm not even able to enable it.

This is the output of
```
sudo lshw -C network
```
is
```
$ sudo lshw -C network

  *-network DISABLED        
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: 00:1f:e1:04:8b:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=4.13.0-37-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:91300000-9130ffff
  *-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: enp2s1
       version: 10
       serial: 00:1e:ec:6d:1c:f4
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff

```
anybody any ideas?

---

### Post by chili555 on 2018-03-28
DISABLED usually means that the hardware switch or key combination is set to turn off the wireless radio. Please run and post:```
rfkill list all
```

---

### Post by matrooswolf on 2018-03-28
Hi chili555,

```
rfkill list all
```

returnes

```
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2018-03-28
> 0: hp-wifi: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]There you are.

Did you try the switch or key combination? Does it have any effect? Please run and post:```
lsmod | grep wmi
```

---

### Post by matrooswolf on 2018-03-28
Hi Chili555,

Thanks! There was indeed a wifi switch. It was lighted blue, so I thought it was on. But it was not. Pushing it activated wifi. Everything works fine now. (Except for me. feel kinda stupid now ;)

---

### Post by chili555 on 2018-03-28
> **matrooswolf said:**
> Hi Chili555,

Thanks! There was indeed a wifi switch. It was lighted blue, so I thought it was on. But it was not. Pushing it activated wifi. Everything works fine now. (Except for me. feel kinda stupid now ;)No worries. If it’s working as expected, we’re happy!

---

