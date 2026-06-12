---
title: "Put wireless card in promiscuous mode."
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by sent17inel on 2008-06-22
This is the laptop i have.  [http://www.circuitcity.com/ccd/productDetail.do?oid=207722&WT.mc_n=3&WT.mc_t=U&cm_ven=COMPARISON%20SHOPPING&cm_cat=CNET&cm_pla=DATAFEED-%3EPRODUCTS&cm_ite=1%20PRODUCT&cm_keycode=3](http://www.circuitcity.com/ccd/productDetail.do?oid=207722&WT.mc_n=3&WT.mc_t=U&cm_ven=COMPARISON%20SHOPPING&cm_cat=CNET&cm_pla=DATAFEED-%3EPRODUCTS&cm_ite=1%20PRODUCT&cm_keycode=3)

im wondering if its possible to put this laptops built in wireless card into promiscuous mode or if im going to have to buy a wireless pcmia card. and if so. what kind of card do u recommend i should buy that has been verified to work in promiscuous mode on ubuntu.?

---

### Post by kevdog on 2008-06-23
Can you list

lsusb

lshw -C network

Trying to find what type of networking card you have!

---

### Post by sent17inel on 2008-06-23
daniel@daniel-laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 03f0:6611 Hewlett-Packard 
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
daniel@daniel-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:07:6c:3a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:25:be:7d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.0.100 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

---

### Post by sent17inel on 2008-06-23
here it told me to run it as a super user so let me post the output using sudo. 


daniel@daniel-laptop:~$ sudo lshw -C network
[sudo] password for daniel: 
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:07:6c:3a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:25:be:7d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.0.100 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
daniel@daniel-laptop:~$

---

### Post by sent17inel on 2008-06-23
nevermind! I got it to work. thanks though!

---

### Post by ubermenschx on 2009-06-04
Now that you got the card to work in promiscuous, how did you do it? I have the same issue.

thank you,

---

### Post by pgn674 on 2009-09-18
> **sent17inel said:**
> nevermind! I got it to work. thanks though!WHAA! How did you do it?

---

### Post by xeffer on 2009-09-24
ive only had ubuntu for a few days and have what might seem like a very stupid question... how do i get my network card OUT of promiscuous mode.... i have an intel/pro wireless 3945agb.

]a speady reply would be much appreciated
xef

---

