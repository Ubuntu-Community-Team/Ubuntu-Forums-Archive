---
title: "cannot see windows machine on ethernet network (wired)"
date: 2019-08-11
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2019-08-11
New desktop just installed Ubuntu 18.04, have access to internet, and printers, but cannot see windows 10 box on the same network (separate machine).   Here is the output of command ```
sudo lshw -C network
```:
```
 *-network UNCLAIMED       
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:fc700000-fc703fff
  *-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 03
       serial: b4:2e:99:3c:d3:b5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.4.0-k duplex=full firmware=0. 6-1 ip=192.168.1.192 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:24 memory:fc600000-fc61ffff ioport:e000(size=32) memory:fc620000-fc623fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:fc570000-fc57ffff memory:fc59c000-fc59ffff memory:fc500000-fc56ffff memory:fc580000-fc59bfff
```
This is the contents of /etc/netplan/01-network-manager-all.yaml:
```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```
and here is output of ```
cat /etc/network/interfaces
```:
auto eth0
iface eth0 inet dhcp

I've tried the suggestions in several posts, installed samba client, and in nautilus I can see "windows network" but it will not expand to show folders I have set up for sharing.
Any and all suggestions greatly appreciated.

ethernet adapter is "Intel Gigabit CT Desktop Adapter"

---

### Post by Morbius1 on 2019-08-11
It's a bug: [https://bugs.launchpad.net/gvfs/+bug/1828107](https://bugs.launchpad.net/gvfs/+bug/1828107)

Actually, it's a bug that was created when they fixed another bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1778322?comments=all](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1778322?comments=all)

The only way around this at the moment is to use the **[COLOR=#0000cd]Connect to Server[/COLOR]** function under [highlight]Other Locations[/highlight] and ask for the server and it's share explicitly:
[ATTACH=CONFIG]283783[/ATTACH]

[ATTACH=CONFIG]283784[/ATTACH]

Or use a cifs mount.

---

