---
title: "Atheros QCA8171, connectivity works fine but zero network traffic and no wake on LAN"
date: 2014-09-03
forum: Networking &amp; Wireless
---

### Post by adriaan1 on 2014-09-03
Up until recently, I was using Ubuntu 12.04. My Qualcomm  Atheros QCA8171 Gigabit Ethernet network card seemed to be working  fine: network traffic and wake on LAN both worked. I just installed Ubuntu 14.04 and the network traffic  only shows zero activity. Also, I can not seem to wake up my computer  remotely via my modem anymore, using wake on LAN. Both ifstat -a and the System Monitor show zero activity. With sudo lshw, I get for the network


*-network
    description: Ethernet interface
    product: QCA8171 Gigabit Ethernet
    vendor: Qualcomm Atheros
    physical id: 0
    bus info: pci@0000:02:00.0
    logical name: eth0
    version: 10
    serial: bc:5f:f4:c9:e9:c6
    size: 1Gbit/s
    capacity: 1Gbit/s
    width: 64 bits
    clock: 33MHz
    capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.178.2 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
    resources: irq:46 memory:f0400000-f043ffff ioport:e000(size=128)

. Furthermore, modinfo alx returns

filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
license:        GPL
description:    Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     15100F26458C5B941F93EBF
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E091sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

. How can I fix the network traffic and wake on LAN?

---

### Post by varunendra on 2014-09-04
Please post back the output of -
```
sudo ethtool eth0
```
And in the meanwhile, to attempt starting the communication, please try -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

To reset it to current state, if the above doesn't help -
```
sudo ethtool -s eth0 speed 1000 duplex full autoneg on
```

---

### Post by adriaan1 on 2014-09-04
Running 'sudo ethtool eth0' I get the output

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: off
    MDI-X: Unknown
    Current message level: 0x000060e4 (24804)
                   link ifup rx_err tx_err hw wol
    Link detected: yes

The command 'sudo ethtool -s eth0 speed 100 duplex full autoneg off' does not seem to solve the issue. The 'ifstat' still gives zero network traffic.

The command 'sudo ethtool -s eth0 speed 1000 duplex full autoneg on' returns

Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg

---

### Post by varunendra on 2014-09-05
What are the outputs of -
```
nm-tool
ping -c4 192.168.178.1
ping -c4 8.8.8.8
```
..in the above state? That is, when autoneg=off, speed=100, duplex=full

---

### Post by adriaan1 on 2014-09-05
This is the output of the three commands, after running 'sudo ethtool -s eth0 speed 100 duplex full autoneg off':

adriaan0913@adriaan0913:~$ sudo ethtool -s eth0 speed 100 duplex full autoneg off
[sudo] password for adriaan0913: 
adriaan0913@adriaan0913:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        BC:5F:F4:C9:E9:C6

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.178.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1

    DNS:             192.168.178.1

  IPv6 Settings:
    Address:         2001:981:441:1:c1cd:d4bc:52ab:5c98
    Prefix:          64
    Gateway:         fe80::9ec7:a6ff:fe0b:a647

    Address:         2001:981:441:1:be5f:f4ff:fec9:e9c6
    Prefix:          64
    Gateway:         fe80::9ec7:a6ff:fe0b:a647

    Address:         fe80::be5f:f4ff:fec9:e9c6
    Prefix:          64
    Gateway:         fe80::9ec7:a6ff:fe0b:a647

    DNS:             fd00::9ec7:a6ff:fe0b:a647


adriaan0913@adriaan0913:~$ ping -c4 192.168.178.1
PING 192.168.178.1 (192.168.178.1) 56(84) bytes of data.
64 bytes from 192.168.178.1: icmp_seq=1 ttl=64 time=2.38 ms
64 bytes from 192.168.178.1: icmp_seq=2 ttl=64 time=6.11 ms
64 bytes from 192.168.178.1: icmp_seq=3 ttl=64 time=23.0 ms
64 bytes from 192.168.178.1: icmp_seq=4 ttl=64 time=2.99 ms

--- 192.168.178.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 2.382/8.637/23.061/8.446 ms
adriaan0913@adriaan0913:~$ ping -c4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=49 time=23.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=49 time=22.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=49 time=23.7 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=49 time=23.7 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 22.467/23.269/23.729/0.517 ms

---

### Post by varunendra on 2014-09-06
> **adriaan1 said:**
> adriaan0913@adriaan0913:~$ ping -c4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=49 time=23.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=49 time=22.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=49 time=23.7 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=49 time=23.7 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 22.467/23.269/23.729/0.517 ms

Everything looks pretty good and with above kind of ping response, I'd say 'Hurray'! - The system is connected to the outer world and it seems with a good speed too.

For the WOL problem, that is due to a regression in alx driver. There was a bug due to which the WOL feature has been temporary removed from the driver.
[https://github.com/torvalds/linux/commit/bc2bebe8de8ed4ba6482c9cc370b0dd72ffe8cd2](https://github.com/torvalds/linux/commit/bc2bebe8de8ed4ba6482c9cc370b0dd72ffe8cd2)
[https://bugzilla.kernel.org/show_bug.cgi?id=61651](https://bugzilla.kernel.org/show_bug.cgi?id=61651)

As such, I guess we only have three options with Linux -

**1)** Try compiling an older driver version in which the feature existed. Something like this (but not 'Exactly' this, as this post was for Fedora Core 20) : [http://www.linuxquestions.org/questions/linux-networking-3/qualcomm-atheros-ar8171-wake-on-lan-issues-4175491464/](http://www.linuxquestions.org/questions/linux-networking-3/qualcomm-atheros-ar8171-wake-on-lan-issues-4175491464/)

**2)** Use a different card whose hardware and driver support WOL

**3)** Wait till it is fixed :|

---

### Post by joelgsf on 2014-10-04
Please, I have the same problema as Adriaan1, and the problem isn`t with the network card but, rather, with System Monitor, which does not show the corresponding traffic. If you`re on a WLan it is Ok, but on an Ethernet connection, no activity is shown. I have 3 computers with Ubuntu 14.04 and all present the same problem.
It is not comprehensible why tere has not been out a patch for this problem.

---

