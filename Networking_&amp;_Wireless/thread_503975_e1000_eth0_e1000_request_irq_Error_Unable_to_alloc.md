---
title: "e1000: eth0: e1000_request_irq Error Unable to allocate MSI interrupt Error: -22"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by professor-g on 2007-07-18
Successfully installed 7.04 Feisty Fawn server for 64 bit.
Master node of 8 node cluster - each node = core 2duo (2.13GHz), 4GB, 80GB SATA
Everything fine.
eth1 configured, up-and-running for internal network (to slave nodes)
eth0 fails to come up - gives following error message :
(eth0 = onboard - GIGABYTE  GA-VM900M)

[  285.662391] e1000: eth0: e1000_request_irq Error Unable to allocate MSI interrupt Error: -22

Any ideas how to rectify this ?
Thx.

---

### Post by fredj on 2007-07-18
No idea really but if we take the error message at face value then it seems the system is unable to allocate
a suitable interrupt to the eth0 card. 
Type 'sudo lshw -class network' in a terminal and post the output.
Also type 'cat /proc/interrupts' and post the output.
Some network cards will only work with a specific interrupt (older types). Some won't share an
interrupt (again only older types I think), some may only accept a standard PC type interrupt  (0-15) and not
the extended interrupts that modern motherboard chipsets can provide.

---

### Post by phalkone on 2007-07-26
I get the same message at start-up. I also get a eth0 hardware error at shutdown. Everything seems to be working, but I would like to get rid of this error.

The results of "sudo lshw -class network":
*-network               
       description: Ethernet interface
       product: 82566DM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:3d:27:ef
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=11.252-1 ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:50200000-5021ffff iomemory:50220000-50220fff ioport:20c0-20df irq:20

the results of "cat /proc/interrupts":
         CPU0       CPU1       
  0:     766881          0   IO-APIC-edge      timer
  1:        341          0   IO-APIC-edge      i8042
  8:          3          0   IO-APIC-edge      rtc
  9:          1          0   IO-APIC-fasteoi   acpi
 12:        103          0   IO-APIC-edge      i8042
 16:        268          0   IO-APIC-fasteoi   libata
 17:          0          0   IO-APIC-fasteoi   uhci_hcd:usb1
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb6
 19:      26924          0   IO-APIC-fasteoi   uhci_hcd:usb4, libata, libata
 20:      10624          0   IO-APIC-fasteoi   eth0
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 22:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3, ehci_hcd:usb7
NMI:          0          0 
LOC:     766789     766788 
ERR:          0
MIS:          0

---

