---
title: "karmic laptop (with huawei e220) wired to ps3 not working"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Darkhorse85 on 2010-01-19
Hi, ive been searching for hours through forums for help with this one, but cant get it right. I am pretty new to ubuntu so please humour my lack of knowlegde.

This is my problem, first of all I cant get my broadcom BCM4311 wireless going and have given up on that. I searched forums for days trying to figure out my problem. So now im trying to connect my PS3 to my laptop using a ethernet cable.

From the laptop's side I have managed to activate Auto eth0, but when I activate the Auto eth0 my mobile broadband default connection (which was already active)(also it is a huawei e220 usb modem) doesn't work even though it says it is connected. The webpage will just try and load indefinitely.

When i switch off my mobile broadband I think the PS3 connects to the laptop but i am not sure because i dont know how to test it except using media servers by installing fuppes. I read the instructions for that and it seems way over my head at this stage. (Even if it does connect then, my problem would still be to connect to the internet0

From the PS3's side i test the INTERNET connection when both Auto eth0 and mobile broadband are connected (although mobile broadband doesnt work at this stage on the laptop) and then it says:
Obtain IP address failed

Any help would be greatly apreciated

Thank you

here are my specs plus ip address:

IP:
darkhorse@darkhorse-laptop:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use 
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        

Specs:
darkhorse@darkhorse-laptop:~$ hwinfo --short
cpu:                                                            
                       AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55, 1600 MHz
                       AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55, 1600 MHz
keyboard:
  /dev/input/event5    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       nVidia GeForce 7150M
sound:
                       nVidia MCP67 High Definition Audio
storage:
                       nVidia MCP67 IDE Controller
                       nVidia MCP67 AHCI Controller
network:
  eth0                 nVidia MCP67 Ethernet
  eth1                 Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  eth1                 Ethernet network interface
  vboxnet0             Ethernet network interface
  ppp0                 Network Interface
disk:
  /dev/sda             ST9120822AS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             Optiarc DVD RW AD-7561A
  /dev/sr1             HUAWEI Mass Storage
usb controller:
                       nVidia MCP67 OHCI USB 1.1 Controller
                       nVidia MCP67 EHCI USB 2.0 Controller
                       nVidia MCP67 OHCI USB 1.1 Controller
                       nVidia MCP67 EHCI USB 2.0 Controller
bios:
                       BIOS
bridge:
                       nVidia MCP67 ISA Bridge
                       nVidia MCP67 PCI Bridge
                       nVidia MCP67 PCI Express Bridge
                       nVidia MCP67 PCI Express Bridge
                       AMD K8 [Athlon64/Opteron] HyperTransport Technology Configuration
                       AMD K8 [Athlon64/Opteron] Address Map
                       AMD K8 [Athlon64/Opteron] DRAM Controller
                       AMD K8 [Athlon64/Opteron] Miscellaneous Control
hub:
                       Linux 2.6.31-17-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.31-17-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.31-17-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.31-17-generic ohci_hcd OHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       Ricoh R5C832 IEEE 1394 Controller
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       nVidia MCP67 Memory Controller
                       nVidia MCP67 SMBus
                       nVidia MCP67 Memory Controller
                       nVidia MCP67 Co-processor
                       Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                       Ricoh R5C843 MMC Host Controller
                       Ricoh R5C592 Memory Stick Bus Host Adapter
                       Ricoh xD-Picture Card Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
  /dev/ttyUSB0         HUAWEI Mobile

---

### Post by Muttley99 on 2010-01-19
What are you trying to do? do you want to share files from your laptop to your PS3? if so;

install mediatomb;

[HTML]sudo apt-get install mediatomb[/HTML]

---

### Post by Darkhorse85 on 2010-01-19
no my primary concern is to connect to the internet, i apologize if i was unclear, as i said im pretty new to this stuff

---

### Post by Darkhorse85 on 2010-01-19
with my ps3 using my laptop through a wired conection

---

