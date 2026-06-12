---
title: "wifi not working"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by lingtaworld on 2010-12-28
I have Ubuntu 9.04 Jaunty Jackalope installed on a HP Pavilion zv5000 previously running Win XP SP3.  The laptop has a wifi on/off button with a small blue LED showing when on. This was working OK with Windows.

I cannot find the equivalent of Windows Device Manager to see if the Network Adaptor (wireless) is working or not or whether a driver is required.

Or maybe download the latest Ubunto 10.10 and install it?

Thanks in advance for your help :)

---

### Post by cariboo on 2010-12-28
the quickest way to check if your wifi device is detected and the correct driver loaded, is to open an Applications->Accessories->terminal and type:

```
sudo lshw -C network
```

you should get something that looks something like this:

```
sudo lshw -C network
[sudo] password for cariboo: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 90:4c:e5:41:e4:2f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.246.2 ip=192.168.1.106 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 18:a9:05:d4:c2:22
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:febc0000-febfffff ioport:ec80(size=128)
```

If you don't have internet access you can create a text file with the above output, by typing the following command:

```
sudo lshw -C network > network.txt
```

then transfer the text file called network.txt to a system with internet access, then paste it in your next post.

---

### Post by lingtaworld on 2010-12-28
Very many thanks for your so-prompt reply.  I shall try this. I should have mentioned that the Ethernet connection is working.

---

### Post by lingtaworld on 2010-12-28
I have done as requested and get this:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

idw@idw-laptop:~$ sudo lshw -C network
[sudo] password for idw: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:40:90:28
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:99:0f:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:9a:09:6c:bd:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
idw@idw-laptop:~$ sudo lshw -C network

It looks as if the Broadcom Corporation Wiis disabled wreless LAN Controller is disabled.

Do you have any ideas how to enable it?
Unfortunately no more from me tonight, many thanks so far!

---

