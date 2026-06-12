---
title: "Installing Linksys WMP110 w/ ndiswrapper"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by vincentjames501 on 2008-10-29
I've been having a few problems lately with my wireless NIC.  I've only been getting about 20-35% connection and will very often stop working periodically.  

I've tried installing ndiswrapper and installing the drivers from my disk from windows xp folder (the inf file).  It seems to have installed fine but I can't click on configure network it says "could not find network configuration tool."  

I also tried to install Wi-Fi Radar (I installed both of these apps from add/remove) and I get could not launch menu item:  Failed to execute child process "su-to-root" (no such file or directory).

Can some one give me pretty detailed directions to getting a better wireless strength?  BTW I am using Ubuntu 8.10 Beta x86.  If you need anything else let me know :)

---

### Post by PinkFloyd102489 on 2008-10-29
Please paste the output of the following commands:

```
sudo lspci
```

```
sudo lshw -C Network
```

---

### Post by vincentjames501 on 2008-10-29
Yes Sir:

Let me know if you need anything else

vincent@ubuntu:~$ sudo lspci
[sudo] password for vincent: 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
vincent@ubuntu:~$ sudo lshw -C Network
  *-network               
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:e5:fb:4e:f3
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.53+Linksys, A Division of Cisc ip=131.151.69.116 latency=128 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:b9:be:e6:27:3b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
vincent@ubuntu:~$

---

