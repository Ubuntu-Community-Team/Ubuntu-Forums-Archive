---
title: "No wireless card found"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by N4WVE on 2009-03-01
I installed Ubuntu as a second partition on my win vista pc. Install went fine but I can't connect to the internet through my wireless card. PLEASE HELP! Without internet I can't even use Ubuntu!

---

### Post by kestrel1 on 2009-03-01
open a terminal & type```
lspci
```& post the result

---

### Post by N4WVE on 2009-03-01
ok...here is the results of two terminal inquiries:

greg@greg-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
greg@greg-desktop:~$ 


And then:
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
greg@greg-desktop:~$ sudo lshw -c network
[sudo] password for greg: 
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:09:e2:64
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:23:54:56:bd:08
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ae:34:72:17:c4:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
greg@greg-desktop:~$ 


What do I need to do to make this work?

---

### Post by kestrel1 on 2009-03-01
Do you get any wireless networks found if you left click on the Network Manager icon in the task bar?

---

### Post by N4WVE on 2009-03-01
No, nothing...

---

