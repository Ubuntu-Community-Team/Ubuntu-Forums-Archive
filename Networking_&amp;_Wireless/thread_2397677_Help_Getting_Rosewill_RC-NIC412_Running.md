---
title: "Help Getting Rosewill RC-NIC412 Running"
date: 2018-08-01
forum: Networking &amp; Wireless
---

### Post by r-peter-2 on 2018-08-01
Hello all! I've been trying for a few hours now to get a Rosewill NIC to register with my Linux system for a while now. I tried the Tehuti Networks driver, then the Rosewill driver from the CD-ROM (tn40xx-0.3.6.14.2.NOMV) (FYI the download on their site is for the wrong NIC). I've got the Rosewill driver installing via DKMS but when I load the module, no extra interfaces appear, and the card appears "UNCLAIMED" in ```
lshw -class net
``` output.

# lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial

```

dkms.conf:
```

PACKAGE_NAME=tn40xx
PACKAGE_VERSION=0.3.6.14.2.NOMV
BUILT_MODULE_NAME[0]="$PACKAGE_NAME"
MAKE[0]="make -C ${kernel_source_dir} M=${dkms_tree}/${PACKAGE_NAME}/${PACKAGE_VERSION}/build"
CLEAN="make -C ${kernel_source_dir} M=${dkms_tree}/${PACKAGE_NAME}/${PACKAGE_VERSION}/build clean"
DEST_MODULE_LOCATION[0]=/extra
REMAKE_INITRD=no
AUTOINSTALL=yes

```

/usr/src/tn40xx-0.3.6.14.2.NOMV# dkms install --force -m tn40xx/0.3.6.14.2.NOMV
```

tn40xx:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.4.0-131-generic/updates/dkms/


depmod....


DKMS: install completed.

```

dmesg:
```
[ 4290.452091] tn40xx: Tehuti Network Driver, 0.3.6.14.2.NOMV
[ 4290.452145] tn40xx: Supported phys :    QT2025 TLK10232 AQR105

```

# lshw -class network
```

  *-network UNCLAIMED
       description: Ethernet controller
       product: Tehuti Networks Ltd.
       vendor: Tehuti Networks Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0600000-d060ffff
  *-network
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: em1
       version: 05
       serial: 40:2c:f4:e9:f9:de
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 ip=10.1.64.68 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:47 memory:dff00000-dff1ffff memory:dff29000-dff29fff ioport:9040(size=32)
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 00
       serial: 40:2c:f4:xx:xx:xx
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=2.1-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 memory:dfa00000-dfa1ffff ioport:5000(size=32) memory:dfa20000-dfa23fff
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: vethd5705a4
       serial: 26:32:3c:xx:xx:xx
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=veth driverversion=1.0 duplex=full link=yes multicast=yes port=twisted pair speed=10Gbit/s
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: vethdc4740a
       serial: 12:a6:92:xx:xx:xx
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=veth driverversion=1.0 duplex=full link=yes multicast=yes port=twisted pair speed=10Gbit/s

```

I *think* the two interfaces are docker containers, but I am not positive. At any rate, the link doesn't come up (no blinken lights).

# ip link
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: em1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 40:2c:f4:e9:f9:de brd ff:ff:ff:ff:ff:ff
3: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 40:2c:f4:e9:f9:df brd ff:ff:ff:ff:ff:ff

```


Does anyone have any pointers? Thanks!

---

### Post by qmpos on 2018-09-01
Did you find a solution to this? I had similar trouble with the StarTech version of this NIC that I now realize is based on the same chipset as the Rosewill that was supposed to replace it. 

I tried this version of the kernel module and got nowhere either: [https://github.com/acooks/tn40xx-driver](https://github.com/acooks/tn40xx-driver)

---

