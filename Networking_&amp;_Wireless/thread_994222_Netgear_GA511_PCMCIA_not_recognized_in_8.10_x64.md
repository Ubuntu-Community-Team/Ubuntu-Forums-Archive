---
title: "Netgear GA511 PCMCIA not recognized in 8.10 x64"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by fejimush on 2008-11-26
I have a Netgear GA511 wired network card plugged into the PCMCIA slot of a Dell Latitude D830 laptop.

Here is what I know (or don't):

```
lspci | grep -i ethernet
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
```

It's the Realtek that is the network card.  The built-in Broadcom works fine.

```
sudo lshw -C network
 *-network DISABLED
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 10
       serial: ff:ff:ff:ff:ff:ff
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical fibre 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=fibre speed=1GB/s
```

```
dmesg | grep eth1
[   14.180473] eth1: RTL8169 at 0xffffc20000654000, ff:ff:ff:ff:ff:ff, XID 7cf0f8ff IRQ 19
[ 1178.792704] eth1: RTL8169 at 0xffffc20000654000, ff:ff:ff:ff:ff:ff, XID 7cf0f8ff IRQ 19
```

```
nm-tool
- Device: eth1 ----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           1000 Mb/s
```

Any help would be greatly appreciated.

Thanks.

---

