---
title: "Connecting to BT Wireless router"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by ShaunC692 on 2007-12-16
Hi I'm hoping someone will be able to help with this I'm attempting to connect to the Internet using via a BT router using ubuntu 7.10 + wireless modem, I'm able to see my SSID number upon entering Network Settings and able to enter my WEP key - however from this point I'm kinda stuck here is the result of:-
lshw -C network
*-network               
       description: Ethernet interface 
       product: RTL8101E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:03:0d:78:bf:a8 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes 
  *-network 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:19:db:9f:e1:02 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 

any help would be greatly appreciated

---

