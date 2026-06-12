---
title: "Kubuntu 18.04.1 decreasing network speed after some update"
date: 2018-12-02
forum: Networking &amp; Wireless
---

### Post by adamweb92 on 2018-12-02
Hi!
On fresh installed system the internet speed approaching the expected values (250/20 Mbit/s). After some update (it is about 1-2 weeks) the download speed lose to ~ 20 Mbit/s.

This phenomenon is exist on both older and newer kernels. Same software environment but different hardware component, then the problem has occurred. That this means for me this phenomena is not caused by hardware problem.

What can cause this and how can it be solved?

You see below output of some network debug commands:

```
lshw: 
[...]
*-network
             description: Ethernet interface
             product: Ethernet Connection (7) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: eno1
             version: 10
             serial: e0:d5:5e:d8:80:d0
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=off broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=half firmware=0.5-4 ip=192.168.0.14 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:128 memory:a1100000-a111ffff
[...]


adam@adam-desktop:~$ dmesg | grep eno1
[    4.412467] e1000e 0000:00:1f.6 eno1: renamed from eth0
[   10.606625] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   10.804270] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   13.702582] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   13.702691] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   19.841054] e1000e: eno1 NIC Link is Up 100 Mbps Half Duplex, Flow Control: None
[   19.841058] e1000e 0000:00:1f.6 eno1: 10/100 speed: disabling TSO
[  904.341772] e1000e: eno1 NIC Link is Down
[  904.377333] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  904.575156] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  909.151672] e1000e: eno1 NIC Link is Up 100 Mbps Half Duplex, Flow Control: None
[  909.151681] e1000e 0000:00:1f.6 eno1: 10/100 speed: disabling TSO
[  909.153598] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[ 8147.365327] VBoxNetFlt: attached to 'eno1' / e0:d5:5e:d8:80:d0
[ 8147.385753] device eno1 entered promiscuous mode
[ 8400.493539] device eno1 left promiscuous mode
[ 8400.588167] device eno1 entered promiscuous mode
[ 8401.976052] device eno1 left promiscuous mode
[ 8402.010766] device eno1 entered promiscuous mode
[ 8421.085114] device eno1 left promiscuous mode
[ 8421.156676] device eno1 entered promiscuous mode
[ 9015.405834] device eno1 left promiscuous mode
[ 9097.114836] VBoxNetFlt: attached to 'eno1' / e0:d5:5e:d8:80:d0
[ 9097.128537] device eno1 entered promiscuous mode
[10753.364676] device eno1 left promiscuous mode
[10998.288485] VBoxNetFlt: attached to 'eno1' / e0:d5:5e:d8:80:d0
[10998.303859] device eno1 entered promiscuous mode
[11197.966575] device eno1 left promiscuous mode
[13418.385002] e1000e: eno1 NIC Link is Down
[13418.481160] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[13418.682810] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[13422.959394] e1000e: eno1 NIC Link is Up 100 Mbps Half Duplex, Flow Control: None
[13422.959402] e1000e 0000:00:1f.6 eno1: 10/100 speed: disabling TSO
[13422.961318] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready


adam@adam-desktop:~$ ethtool -i eno1
driver: e1000e
version: 3.2.6-k
firmware-version: 0.5-4
expansion-rom-version: 
bus-info: 0000:00:1f.6
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no

```

---

### Post by mitesh.agrwl on 2018-12-04
> **adamweb92 said:**
> Hi!
On fresh installed system the internet speed approaching the expected values (250/20 Mbit/s). After some update (it is about 1-2 weeks) the download speed lose to ~ 20 Mbit/s.

This phenomenon is exist on both older and newer kernels. Same software environment but different hardware component, then the problem has occurred. That this means for me this phenomena is not caused by hardware problem.

What can cause this and how can it be solved?

You see below output of some network debug commands:

```
lshw: 
[...]
*-network
             description: Ethernet interface
             product: Ethernet Connection (7) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: eno1
             version: 10
             serial: e0:d5:5e:d8:80:d0
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: **autonegotiation=off** broadcast=yes driver=e1000e driverversion=3.2.6-k **duplex=half** firmware=0.5-4 ip=192.168.0.14 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:128 memory:a1100000-a111ffff
[...]


adam@adam-desktop:~$ dmesg | grep eno1
[    4.412467] e1000e 0000:00:1f.6 eno1: renamed from eth0
[   10.606625] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   10.804270] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   13.702582] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   13.702691] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   19.841054] e1000e: eno1 NIC Link is Up 100 Mbps Half Duplex, Flow Control: None
[   19.841058] e1000e 0000:00:1f.6 eno1: 10/100 speed: disabling TSO
[  904.341772] e1000e: eno1 NIC Link is Down
[  904.377333] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  904.575156] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  909.151672] e1000e: eno1 NIC Link is Up 100 Mbps Half Duplex, Flow Control: None
[  909.151681] e1000e 0000:00:1f.6 eno1: 10/100 speed: disabling TSO
[  909.153598] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[ 8147.365327] VBoxNetFlt: attached to 'eno1' / e0:d5:5e:d8:80:d0
[ 8147.385753] device eno1 entered promiscuous mode
[ 8400.493539] device eno1 left promiscuous mode
[ 8400.588167] device eno1 entered promiscuous mode
[ 8401.976052] device eno1 left promiscuous mode
[ 8402.010766] device eno1 entered promiscuous mode
[ 8421.085114] device eno1 left promiscuous mode
[ 8421.156676] device eno1 entered promiscuous mode
[ 9015.405834] device eno1 left promiscuous mode
[ 9097.114836] VBoxNetFlt: attached to 'eno1' / e0:d5:5e:d8:80:d0
[ 9097.128537] device eno1 entered promiscuous mode
[10753.364676] device eno1 left promiscuous mode
[10998.288485] VBoxNetFlt: attached to 'eno1' / e0:d5:5e:d8:80:d0
[10998.303859] device eno1 entered promiscuous mode
[11197.966575] device eno1 left promiscuous mode
[13418.385002] e1000e: eno1 NIC Link is Down
[13418.481160] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[13418.682810] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[13422.959394] e1000e: eno1 NIC Link is Up 100 Mbps Half Duplex, Flow Control: None
[13422.959402] e1000e 0000:00:1f.6 eno1: 10/100 speed: disabling TSO
[13422.961318] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready


adam@adam-desktop:~$ ethtool -i eno1
driver: e1000e
version: 3.2.6-k
firmware-version: 0.5-4
expansion-rom-version: 
bus-info: 0000:00:1f.6
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no

```

Check highlighted text. The autonegotiation is turned off and the duplex is set to half. This is not desirable. Run the command ```
ethtool -s autoneg on duplex full
```

and restart the network.

---

