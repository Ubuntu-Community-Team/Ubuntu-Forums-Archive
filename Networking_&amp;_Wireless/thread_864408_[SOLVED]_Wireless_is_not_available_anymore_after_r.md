---
title: "[SOLVED] Wireless is not available anymore after reboot"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Friccy on 2008-07-19
Hi everyone!
I just bought a new HP Pavilion laptop and installed Hardy on it.
Everything is OK, but the wireless networks disappears every time I am rebooting the laptop. 
So it works just on fresh install and I can not stop the machine because there is no more wireless after that.
Do you have any idea why is it? 
Thanks!

---

### Post by sputnikkk on 2008-07-19
same problem here but with Linksys WMP54G and desktop.

I just have to enter the Network Manager GUI and change it from WPA to WPA2 and re enter the passkey/phrase, and it reconnects.

From the deksktop GUI

System --> Administration ---> Network

---

### Post by Ayuthia on 2008-07-19
> **Friccy said:**
> Hi everyone!
I just bought a new HP Pavilion laptop and installed Hardy on it.
Everything is OK, but the wireless networks disappears every time I am rebooting the laptop. 
So it works just on fresh install and I can not stop the machine because there is no more wireless after that.
Do you have any idea why is it? 
Thanks!

Do you know if you had to install anything to make your wireless work?  If you could, can you post the results of the following from the Terminal:
```
lshw -C network
```
It will help us see what wireless card you are using and what driver it is trying to use.

---

### Post by Friccy on 2008-07-20
Hello!
I have installed some drivers that the package manager has found (a Broadcom driver).
It said that it is enabled and in use.
Now that I have restarted the laptop, there is no wireless signal, but on the XP laptop there is.
Here is the output you have asked:
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:d3:aa:4c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
Thanks for your help!

---

