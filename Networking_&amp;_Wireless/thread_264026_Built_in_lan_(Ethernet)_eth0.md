---
title: "Built in lan (Ethernet) eth0"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by simbiwa on 2006-09-24
[COLOR="SeaGreen"]{I have posted the same topic in Kubuntu forum but as I am not getting the problem solved , I am trying it here as well)[/COLOR]

I am using ASUS P4V8X-MX motherboard with a built in Lan, everything was working perfectly , I was able to connect to internet and my area network using the ethernet connection.

The problem started when I tried a 128 mb Graphics card in the AGP slot.
The system at the boot time cried out KERNEL PANIC ! 

I removed the graphics card and went back to the way I was using it, now I am unable to see the ethernet or lan and am unable to connect to the network or Internet.

[COLOR="Red"]I tried ifconfig -a and I can only see details of lo(loopback) and nothing else no eth0.[/COLOR]

As I have XP also installed , there is no problem, Lan is working fine.

How can I make Linux see the builtin lan and be able to connect using the ethernet to network.? Any help will be greatly appreciated.


**lspci output:** 
00:12.0 Ethernet Controller: VIA technologies, Inc. VT6102 [rhine-II] (rev 78)



The motherboard specification states :10/100Mb fast ethernet with external VIA 
VT6103 PHY


**Entries in my /etc/iftab**
eth0 mac 00:15:f2:d3:8a:a7 arp 1


**result of lshw:** *-network UNCLAIMED
description: Ethernet controller
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@00:12.0
version: 78
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
resources: ioport:d800-d8ff iomemory:febffc00-febffcff irq:193



**Entries in /etc/networks/interface:**
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.35.15
netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp



**and when I typed sudo ifup eth0:**simbiwa@station14:~$ sudo ifup eth0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
simbiwa@station14:~$ 

I managed to check the /var/log files and am posting something which i suspect is the real cause as the system is reading the MAC address as invalid 

**log of 02-sep-2006**08:35:16 localhost kernel: [4294697.863000] FDC 0 is a post-1991 82077
Sep 2 08:35:16 localhost kernel: [4294698.380000] Real Time Clock Driver v1.12
Sep 2 08:35:16 localhost kernel: [4294698.428000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
Sep 2 08:35:16 localhost kernel: [4294698.428000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 193
Sep 2 08:35:16 localhost kernel: [4294698.428000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 1
Sep 2 08:35:16 localhost kernel: [4294698.428000] eth0: VIA Rhine II at 0x1d800, [COLOR="Blue"]00:15:f2:d3:8a:a7[/COLOR], IRQ 193.
Sep 2 08:35:16 localhost kernel: [4294698.429000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1. )

In the above eth0 is  up and everything works fine but after that

**Log of 20-Sep-2006**
Sep 20 08:56:57 localhost kernel: [4294694.654000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 201
Sep 20 08:56:57 localhost kernel: [4294694.654000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 9
Sep 20 08:56:57 localhost kernel: [4294694.654000] [COLOR="Red"]Invalid MAC address
Sep 20 08:56:57 localhost kernel: [4294694.654000] via-rhine: probe of 0000:00:12.0 failed with error -5[/COLOR]

The correct address as on the sticker on the mobo shows as 0015f2d38aa7 and thats what is showing in /etc/iftab file.

In xp I managed to set the mac address in the proprties of my ethernet card but how to do that in Linux?


What could be error -5? How to make the eth0 see the correct mac address?

I have tried adding this in the /etc/network/interfaces file 
hwaddress ether 00:15:f2:d3:8a:a7

but it does not work. Any suggestions will be helpful.

---

### Post by simonjames on 2008-07-20
I am getting the exact same problem any help will be appreciated.

---

