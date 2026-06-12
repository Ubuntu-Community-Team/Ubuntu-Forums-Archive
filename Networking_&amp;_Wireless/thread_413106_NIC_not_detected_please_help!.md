---
title: "NIC not detected please help!"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by Jageye on 2007-04-18
Hi, i just installed edgy onto my mums computer, and the network card wasnt detected. 
The mother board is a Gigabyte M61VME-S2 rev2.0 
The onboard network card works fine in windows but not in ubuntu
I dont know exactly what chipset it is but it says nVidia Geforce 6100/nForce 400.
It does say it has Realtek 8201 as the ethernet chipset, but im not 100% sure

Thanks in advance for any help

Dan

---

### Post by dbott67 on 2007-04-18
Can you post the output of the following commands (you may need to copy them to USB/floppy disk and then post them from a working computer):
```
dbott@edgy:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.37 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```
```
dbott@edgy:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

```
and 
```
dbott@edgy:~$ lspci -n
00:00.0 0600: 8086:27a0 (rev 03)
00:01.0 0604: 8086:27a1 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 01)
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.3 0604: 8086:27d6 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:2448 (rev e1)
00:1f.0 0601: 8086:27b9 (rev 01)
00:1f.2 0101: 8086:27c4 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
01:00.0 0300: 1002:7145
03:00.0 0200: 14e4:170c (rev 02)
03:01.0 0c00: 1180:0832
03:01.1 0805: 1180:0822 (rev 19)
03:01.2 0880: 1180:0843 (rev 01)
03:01.3 0880: 1180:0592 (rev 0a)
03:01.4 0880: 1180:0852 (rev 05)
0b:00.0 0280: 14e4:4311 (rev 01)

```

This will help determine the NIC and chipset.

You can redirect the output of the above commands into a file by using the following commands:
```
sudo lshw -C network > lshw.txt
lspci > lspci.txt
lspci -n > lspcin.txt
```

There will be 3 files in the home directory with the .txt names above.  Copy to USB or floppy and then post them up here.

-Dave

---

### Post by Jageye on 2007-04-18
Ok this is what i got..

```
sudo lshw -C network
``` brought back nothing

lspci 
```
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)
00:07.0 Bridge: nVidia Corporation Unknown device 03ef (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0391 (rev a1)

```

lspci -n
```
00:00.0 0500: 10de:03ea (rev a1)
00:01.0 0601: 10de:03e0 (rev a2)
00:01.1 0c05: 10de:03eb (rev a2)
00:01.2 0500: 10de:03f5 (rev a2)
00:02.0 0c03: 10de:03f1 (rev a2)
00:02.1 0c03: 10de:03f2 (rev a2)
00:04.0 0604: 10de:03f3 (rev a1)
00:05.0 0403: 10de:03f0 (rev a2)
00:06.0 0101: 10de:03ec (rev a2)
00:07.0 0680: 10de:03ef (rev a2)
00:08.0 0101: 10de:03f6 (rev a2)
00:0c.0 0604: 10de:03e9 (rev a2)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
02:00.0 0300: 10de:0391 (rev a1)

```

thanks again for the help
Dan

---

### Post by dbott67 on 2007-04-18
Well, the output of those commands does not indicate any network card.  :(

What version of Ubuntu are you running?  I did some searching and there are others with this chipset that have troubles, but no solution other than buying a new NIC for $15.00 or so.

I think that may be your best solution.

-Dave

---

### Post by Jageye on 2007-04-18
yea after a bit of searching i came to the same solution.

Thanks again for the help, ill just go and get a new one


Dan

---

### Post by dbott67 on 2007-04-18
Perhaps a kernel upgrade may work:
[http://ubuntuforums.org/showthread.php?t=355173&highlight=realtek+8201](http://ubuntuforums.org/showthread.php?t=355173&highlight=realtek+8201)

or this:
[http://ubuntuforums.org/showthread.php?t=290828&highlight=realtek+8201](http://ubuntuforums.org/showthread.php?t=290828&highlight=realtek+8201)

-Dave

---

### Post by josephus on 2007-04-18
i responded to a similar post with slightly different chipset, but i think the solution is the same:

[http://ubuntuforums.org/showthread.php?t=411540](http://ubuntuforums.org/showthread.php?t=411540)

since feisty is released today, i think that is the easiest solution.

---

