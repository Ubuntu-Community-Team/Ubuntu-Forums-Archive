---
title: "[SOLVED] wifi card dies when copying to windows machine"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by shane19174 on 2008-08-20
I'm relatively new to Linux and Ubuntu (ca. 2 months), running 8.04.1 with very few problems except for integration into an existing Windows home network. Specifically, I'm having a very strange issue (which I couldn't find mentioned on the forums) where when I connect to a shared folder on an XP machine via Samba and copy files from Ubuntu over the network, my wireless card (Belkin wireless G USB) simply stops working until I unplug it and plug it back in. I get a message that the connection timed out and the signal strength monitor at the top right drops down to 0%. Note that I have no problem mounting the share. I just can't send files across (in fact, a recent attempt to send a folder containing a few jpegs managed to send one or two of the pictures before the card died). Also, this is not occuring sporadically but every time I transfer files from my Ubuntu machine to the XP machine. (And it's not a firewall issue: I disabled the firewall on the XP box and nothing changed.)

Like I said, I'm new to all this, so I don't know exactly what I need to post in order to narrow down the cause.

Please let me know and I'll add whatever's necessary.

---

### Post by shane19174 on 2008-08-20
Maybe this info will help (?):

lsusb gives me this:

Bus 006 Device 006: ID 050d:705a Belkin Components 
Bus 006 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 006 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


lspci gives me this:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0401 (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


And lshw -C Network reports this:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:21:be:d0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1c:df:9d:88:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.178.20 multicast=yes wireless=IEEE 802.11g


Thanks in advance for any help you might offer.

---

### Post by shane19174 on 2008-08-20
Just thinking about this issue a little more.... Does it help at all to know that I first noticed this under kernel 2.6.24-20-generic, and that it persists under the 2.6.24-21 which I installed last night?

Again, thanks in advance

---

### Post by shane19174 on 2008-08-27
Anyway, it's working now. I don't know if this was the solution, but I got rid of the 2.6.24-20 and -21 kernels, went back to the standard -19, and everything's OK. (I know, I shouldn't have strayed from this kernel in the first place, but it was part of a desperate attempt to solve a graphics card problem. Now both problems are solved, though...).

---

