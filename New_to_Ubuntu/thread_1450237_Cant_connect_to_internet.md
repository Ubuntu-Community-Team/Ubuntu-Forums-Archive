---
title: "Cant connect to internet"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by ryanuberpwnage on 2010-04-08
Hello, I just got Ubuntu 9.10 yesterday, and im unable to connect to the internet. i looked in system > administration > hardware , but it said i had no drivers or something. im not sure what to do, it shows all the other wireless internet connections in my area, except my own, but i attempted to connect to another wireless thing and it didnt work either.

---

### Post by Psumi on 2010-04-08
> **ryanuberpwnage said:**
> Hello, I just got Ubuntu 9.10 yesterday, and im unable to connect to the internet. i looked in system > administration > hardware , but it said i had no drivers or something. im not sure what to do, it shows all the other wireless internet connections in my area, except my own, but i attempted to connect to another wireless thing and it didnt work either.

run lspci in terminal. Tell us the output.

---

### Post by ryanuberpwnage on 2010-04-08
> **Psumi said:**
> run lspci in terminal. Tell us the output.
 so heres the terminal output thing
 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller

---

### Post by Psumi on 2010-04-08
try lsusb in terminal and tell us the output.

---

### Post by ryanuberpwnage on 2010-04-08
> **Psumi said:**
> try lsusb in terminal and tell us the output.
 
heres the output
 
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13fe:3123 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 14b2:3c27 Atheros Communications Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Psumi on 2010-04-08
> **ryanuberpwnage said:**
> Bus 002 Device 002: ID 14b2:3c27 Atheros Communications Inc

We got a winner!

Check this: [http://ubuntuforums.org/showpost.php?p=8762375&postcount=9](http://ubuntuforums.org/showpost.php?p=8762375&postcount=9)

---

### Post by ryanuberpwnage on 2010-04-09
It shows all the internet connections in my area now, but it wont let me connect

---

### Post by anewguy on 2010-04-09
Is your router showing?  If not, is the router set to not broadcast the ESSID?  If so, you have to manually start a new connection and specify the ESSID.

Does your router have MAC filtering enabled?  If so, is the MAC address of your adapter in the router MAC list?

Does your router have WEP, WPA, or any other type enabled?  If so, you need to select the correct type and enter the correct password, passphrase, etc.

Dave ;)

---

### Post by ryanuberpwnage on 2010-05-03
i just switched to ubuntu 10.04 and the same problem still occurs, except on 9.10 the blacklisting was able to at least show me my wireless connection, now when i try to blacklist it wont show me any of the local connections. the problem may be linked to the router which is a linksys WRT160n. it also seems makefiles do not work for some reason and i was unable to download yum or a compiler to get the appropriate driver for my wireless usb

---

