---
title: "Hp Envy 14 - Wireless not working (ubuntu 14.04)"
date: 2014-07-07
forum: Networking &amp; Wireless
---

### Post by demo.b on 2014-07-07
Have not been able to use wireless on Ubuntu 14.04, my laptop is Hp envy 14. I have tried everything possible in the last 2 days. 
There are lots of issues with my laptop or should i say wireless device. Please see all issues below.


 1. Somethings the wireless device does not showup at top right of the screen and whenever it shows, i get messages like "device not ready", "Wireless is disabled by hardware switch" or the device will be grayed out.
 2. When system is booting, i noticed this error "iwlwifi failed to load firmware chunk"
 3. Whenever wireless is enabled, the system becomes very slow and drags.
 4. I always boot to bios, reset settings to default before the system will recognize the wireless. And this leads to point 3 above.


Please i need help!


    demob@Amazo:~$ sudo lshw -C network
    [sudo] password for demob: 
      *-network               
           description: Ethernet interface
           product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:02:00.0
           logical name: eth0
           version: 03
           serial: 64:31:50:94:41:b3
           size: 100Mbit/s
           capacity: 1Gbit/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
           resources: irq:41 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff memory:c0420000-c043ffff
      *-network
           description: Network controller
           product: Centrino Advanced-N 6200
           vendor: Intel Corporation
           physical id: 0
           bus info: pci@0000:03:00.0
           version: 35
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress cap_list
           configuration: driver=iwlwifi latency=0
           resources: irq:45 memory:c2400000-c2401fff
    
    
    demob@Amazo:~$ iwlist scan
    eth0      Interface doesn't support scanning.
    
    lo        Interface doesn't support scanning.

---

### Post by chili555 on 2014-07-08
Let's have a look at:```
dmesg | grep iwl
ls -al /lib/firmware | grep iwlwifi
rfkill list all
```Thanks.

---

