---
title: "[SOLVED] Ethernet not working after update"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by cherokeewheeler on 2016-02-15
After updating my Ubuntu 14.04 my internet stopped working. Like I said I'm plugged in, and I know my router is working because all my other computers that run W7 still work fine. I have been dual booting Ubuntu and W7 for about 4 months now so I'm not to good at Terminal yet

In system settings/network it says "the system network services are not compatible with this version."

I entered code= sudo lshw -C network

al@FSX:~$ sudo lshw -C network 
[sudo] password for al: 
  *-network DISABLED       
       description: Ethernet interface 
       product: 82579V Gigabit Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth1 
       version: 05 
       serial: f4:6d:04:53:7d:6b 
       capacity: 1Gbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:51 memory:f7f00000-f7f1ffff memory:f7f29000-f7f29fff ioport:f080(size=32) 
  *-network DISABLED 
       description: Ethernet interface 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:0e:00.0 
       logical name: eth0 
       version: 06 
       serial: f4:6d:04:53:6a:15 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:50 ioport:9000(size=256) memory:ea104000-ea104fff memory:ea100000-ea103fff 
al@FSX:~$ 

thank you for the help

---

### Post by cherokeewheeler on 2016-02-15
fixed the problem with [http://ubuntuforums.org/showthread.php?t=2311705](http://ubuntuforums.org/showthread.php?t=2311705)

---

