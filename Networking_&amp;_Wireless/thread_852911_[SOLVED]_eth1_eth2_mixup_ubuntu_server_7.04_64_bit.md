---
title: "[SOLVED] eth1 eth2 mixup ubuntu server 7.04 64 bit"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by yamato08 on 2008-07-08
Ok, this has been driving me crazy for the last week.
```
$ lspci | grep -i ethernet
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
06:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
```
I have one onboard (Broadcom), and one RealTek 8029 pci ethernet adapter in this server. Obviously this is seen. But something strange happens in dmesg:
```
$ dmesg | grep -i eth[0-9]
[  224.423904] eth0: RealTek RTL-8029 found at 0x2400, IRQ 17, 00:00:21:F5:D2:48.
[  224.670035] eth1: Tigon3 [partno(BCM95721) rev 4101 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:0d:60:17:db:54
[  224.670044] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[  224.670047] eth1: dma_rwctrl[76180000] dma_mask[64-bit]
[  260.114418] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  262.787370] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[  262.787375] tg3: eth0: Flow control is on for TX and on for RX.
[  262.789287] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  273.624914] eth0: no IPv6 routers present

```
Somehow during boot, eth0 is first assigned to the pci card eth1 to onboard, and later to eth0 to onboard controller. And what happens to eth1? Dissapears.
```
$ ifconfig -s -a
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR   TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0    689300      0      0      0   797755      0      0      0 BMRU
eth2   1500 0         0      0      0      0        0      0      0      0 BM
lo    16436 0  12625190      0      0      0 12625190      0      0      0 LRU

```
Now you think "yeah, because you assigned it eth2 in interfaces":
```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.XX.1
        netmask 255.255.255.0
        broadcast 192.168.XX.255
        network 192.168.XX.0
        gateway 192.168.XX.253
        post-up iptables-restore < /etc/iptables.up.rules
        # dns-* options are implemented by the resolvconf package, if installed


iface eth1 inet static
        address 192.168.YY.1
        netmask 255.255.255.0
        broadcast 192.168.YY.255
        network 192.168.YY.0
        # dns-* options are implemented by the resolvconf package, if installed
auto eth1

```(I put XX and YY to protect the innocent)
And whats this??
```
$ sudo ifdown eth1
ifdown: interface eth1 not configured
$ sudo ifdown eth2
ifdown: interface eth2 not configured

```
Anyone help me?

Some extra info, network card modules are properly loaded.
```
$ uname -a
Linux sandikli 2.6.20-17-generic #2 SMP Mon Jun 9 19:21:17 UTC 2008 x86_64 GNU/Linux
$ lsmod | grep ne2k
ne2k_pci               13792  0
8390                   12416  1 ne2k_pci
$ lsmod | grep tg
tg3                   114436  0
s$ sudo lshw -C Network
Password:
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 11
       serial: 00:0d:60:17:db:54
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72.1 duplex=full firmware=5721-v3.29a ip=192.168.XX.1 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: iomemory:d0100000-d010ffff irq:16
  *-network DISABLED
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth2
       version: 00
       serial: 00:00:21:f5:d2:48
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 multicast=yes
       resources: ioport:2400-241f irq:17

```

Basically, I want to have an eth1. That will be the pppoe interface. Right now I can't even add iptables rules because of this mixup.

---

### Post by yamato08 on 2008-07-08
Ok, solved. The problem seems to be in the file:
```

$ cat iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0d:60:17:db:54 arp 1
eth1 mac 00:00:21:f5:d2:48 arp 1

```
The hw address of eth1 was somehow wrong, which caused confusion in the kernel.

---

