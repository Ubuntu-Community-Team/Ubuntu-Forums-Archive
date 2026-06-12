---
title: "Intel Corporation Centrino Advanced-N 6200 (rev 35), wireless turned off"
date: 2017-11-29
forum: Networking &amp; Wireless
---

### Post by jothezero on 2017-11-29
Hello, I have searching around a lot to fix my wireless problem, sadly, nothing has worked so far.

My card
> 
$ lspci | grep -i net
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)


rfkill, notice that it does not show up, wlp3s0
> 
$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes


sudo lshw -C network


> 
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 06
       serial: f0:de:f1:15:3b:86
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.12-1 ip=192.168.0.107 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:24 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1820(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 35
       serial: 00:27:10:cf:2e:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-40-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:28 memory:f2400000-f2401fff


Some errors in journalctl

> 

Nov 29 13:25:35 zero-ThinkPad-T410 NetworkManager[941]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Nov 29 13:25:35 zero-ThinkPad-T410 NetworkManager[941]: <warn>  [1511979935.4722] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.E







---

