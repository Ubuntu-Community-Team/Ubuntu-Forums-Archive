---
title: "Network problems Qualcom Atheros Killer E2200 - Trusty with kernel 3.16.0-45-generic"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by roberto53 on 2016-01-06
Hi all, Just installed new mainboard  Msi-Z87 and have network problems, it works once every 10 reboot, 
Ubuntu is trusty with kernel 3.16.0-45-generic (64bit )
The interface is a Qualcom Atheros Killer E2200. Read in internet that some year ago it had problems, but with new kernel it should be solved 

In dmesg no errors 
```
[    0.653893] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [d4:3d:7e:da:4c:89]
[   13.031523] alx 0000:03:00.0: irq 47 for MSI/MSI-X
[   13.032385] alx 0000:03:00.0 p3p1: NIC Up: 100 Mbps Full
```

ifconfig seems it doesn't have ip addr

```
p3p1      Link encap:Ethernet  HWaddr d4:3d:7e:da:4c:89  
          inet6 addr: fe80::d63d:7eff:feda:4c89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:94168 (94.1 KB)
          Interrupt:19 
```

Any clue about make it works ?

Add lshw info

```
 root@rob-MS-7821:/etc/default$ lshw -C network  *-network               
       description: Ethernet interface
       product: Killer E2200 Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: p3p1
       version: 13
       serial: d4:3d:7e:da:4c:89
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:f7100000-f713ffff ioport:d000(size=128)

root@rob-MS-7821:/etc/default$ lspci -nnk | grep -iA2 net; dkms status
03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 13)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7821]
	Kernel driver in use: alx
```
virtualbox-guest, 4.3.10, 3.16.0-45-generic, x86_64: installed

---

