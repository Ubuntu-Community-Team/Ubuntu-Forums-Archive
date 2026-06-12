---
title: "EP45-DS3R: Two ethernet ports / twice the trouble"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by OsireS on 2008-10-11
Hi all

I've had this problem since I installed Hardy Heron and I was hoping someone could help me out. My motherboard, the EP45-DS3R has two ethernet ports both being of the Realtek 8169. The issue arises in that only one is ever detected correctly .. and it randomly swaps with each reboot so everytime I boot up I need to do a "lshw -C network" find out if eth0 or eth1 was detected correctly and switch my cable. As you can imagine this is a real pain. Anybody else experiencing this issue or know how to solve it? I've ruled out driver problems as I used the r8169 driver that came with HH and got the latest one from Realtek both having the same result.

Output of lshw is as follows:

```
  *-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: ff
       serial: 00:1d:7d:0a:2e:77
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:1d:7d:0a:2e:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.64 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

Where you can see that one ethernet interface is picked up as *-generic  with an illegal vendor ID. Now both ethernet ports are exactly the same and chances are on reboot eth0 will work fine and eth1 will come up as eth0 is now.

This drives me a little nuts so hopefully someone can help me out.

---

### Post by cariboo on 2008-10-11
Is there a way of possiblely disabling one of the interfaces in the BIOS?

Jim

---

