---
title: "Intel Centrino n 2230 wireless driver problem"
date: 2013-10-16
forum: Networking &amp; Wireless
---

### Post by Raxeee on 2013-10-16
I have Intel Centrino N 2230 WiFi card and I tried to download iwlwifi tar from Ubuntu wireless drivers and then I copied its .ucode to firmware folder and then I ran modprobe -r lawgn andmodprobe lawgn. It didn't run, even after restart. Then I updated the compat-drivers but still didn't work.
I tried rfkill unblock all, checked the button, etc. but it didn't show up in airmon-ng andiwconfig.
Can anyone kindly help because i have been searching and asking for this to many ubuntu users and experts but no one has made me successful instead they went away quietly. So please solve my problem!
This is the output of mine:

lshw -C network 

*-network               
   description: Ethernet interface
   product: RTL8111/8168B PCI Express Gigabit Ethernet controller
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0.2
   bus info: pci@0000:07:00.2
   logical name: eth0
   version: 0a
   serial: 28:92:4a:1d:af:a1
   size: 100MB/s
   capacity: 1GB/s
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
   resources: irq:41 ioport:2000(size=256) memory:61404000-61404fff memory:61400000-61403fff
*-network UNCLAIMED
   description: Network controller
   product: Intel Corporation
   vendor: Intel Corporation
   physical id: 0
   bus info: pci@0000:08:00.0
   version: c4
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list
   configuration: latency=0
   resources: memory:61500000-61501fff


iwconfig  

lo        no wireless extensions.
eth0      no wireless extensions.


airmon-ng   

Interface   Chipset     Driver


lsb_release -a; uname -a  

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:    10.04
Codename:   lucid
Linux bt 2.6.38 #1 SMP Thu Mar 17 20:52:18 EDT 2011 i686 GNU/Linux

---

### Post by mörgæs on 2013-10-17
New hardware and old software is a bad mix. Your best option is to begin with a clean install of 13.10. 

Please write again if you still have the problem after that.

---

### Post by Raxeee on 2013-10-18
i cant install the new update. I have to make it working on the same 10.04. Is there any way?

---

### Post by mörgæs on 2013-10-19
I'm not talking of an update, but a clean install (erasing the old system completely).

---

### Post by Raxeee on 2013-10-19
no i cant format it bkuz its installed side by side wid windows if i do so it will although dont delete the windows but will delete its boot loader.....dats the problem i cant....!

---

### Post by mörgæs on 2013-10-20
The boot loader will either be restored during the new Buntu installation or Boot-Repair will solve it.

---

