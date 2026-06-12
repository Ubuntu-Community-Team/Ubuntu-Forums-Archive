---
title: "Wireless and less and less"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by encyclic on 2009-08-01
okokok...

I am trying to get my wireless up and running on a Toshiba Sat- L550
I`ve gone to Realtek and Toshiba to find drivers and we found them at the Toshiba site

When I use Windows Wireless Drivers program ..computersez...no
not the correct .inf file...grrr.

Terminal program sez-
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:f5:af:bc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.105 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:09:5a:63:02:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

sooooooooooooooo...now what?

thanks in advance

---

### Post by swoll1980 on 2009-08-01
downloaded the linux driver r8101-1.011.00.tar.bz2 from the Realtek site. Then maybe [this]("ubuntuforums.org/archive/index.php/t-1054480.html") will help.

---

