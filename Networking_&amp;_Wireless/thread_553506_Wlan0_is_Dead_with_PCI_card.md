---
title: "Wlan0 is Dead with PCI card"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by bendystraw on 2007-09-17
Ok so i got it to work and i think i removed the driver and wlan0 got erased and i figured out i needed that so i put the card back in and now its no appearing. I loaded the driver 

I have a D-Link DWA-542 btw


So now im trying to fix this and its really starting to get frustrated im using this site to help set up my driver 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-ee2bb70901c2ad8d87232e99dd6a58db1abe61f1](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-ee2bb70901c2ad8d87232e99dd6a58db1abe61f1)

Also if you know anything about wireless network device, it dosnt show up anymore in my System > Administration, if you know how to fix this please help 



Thanks in Advance
:popcorn:

---

### Post by kevdog on 2007-09-17
That page you are using is really out of date.  Lets just go back to basics and everything should work.

Lets find the chipset and driver assigned to your card.  Please post
lshw -C network
lspci -nn

We will start there.  Installing ndiswrapper from repository is usually not my recommended approach since the version offered is so old.  We can deal wtih this later if needed however.

---

### Post by bendystraw on 2007-09-18
lshw -C network
> 
  *-network
       description: Ethernet interface
       product: 82573V Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 03
       serial: 00:13:20:a3:13:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 ip=192.168.2.3 multicast=yes
       resources: iomemory:90100000-9011ffff ioport:1000-101f irq:66
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@05:02.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       resources: iomemory:90000000-9000ffff irq:11



lspci -nn
> 
0000:00:00.0 0600: 8086:2770
0000:00:01.0 0604: 8086:2771
0000:00:1b.0 0403: 8086:27d8 (rev 01)
0000:00:1c.0 0604: 8086:27d0 (rev 01)
0000:00:1c.2 0604: 8086:27d4 (rev 01)
0000:00:1c.3 0604: 8086:27d6 (rev 01)
0000:00:1d.0 0c03: 8086:27c8 (rev 01)
0000:00:1d.1 0c03: 8086:27c9 (rev 01)
0000:00:1d.2 0c03: 8086:27ca (rev 01)
0000:00:1d.3 0c03: 8086:27cb (rev 01)
0000:00:1d.7 0c03: 8086:27cc (rev 01)
0000:00:1e.0 0604: 8086:244e (rev e1)
0000:00:1f.0 0601: 8086:27b8 (rev 01)
0000:00:1f.1 0101: 8086:27df (rev 01)
0000:00:1f.2 0101: 8086:27c0 (rev 01)
0000:00:1f.3 0c05: 8086:27da (rev 01)
0000:01:00.0 0300: 1002:5b63
0000:01:00.1 0380: 1002:5b73
0000:02:00.0 0200: 8086:108b (rev 03)
0000:05:02.0 0280: 168c:0023 (rev 01)
0000:05:05.0 0c00: 104c:8024


There it is and thank you for taking the time to help me

*Edit*
I have 2 wireless cards installed
a Belkin N1 (80001)
and the one i think i have to use D-Link DWA 542

---

### Post by kevdog on 2007-09-19
How about just lspci -n

I can you you dont have a driver assigned to the card with the atheros chipset.  Just trying to figure out which of those two cards it is.

---

### Post by bendystraw on 2007-09-19
> **kevdog said:**
> How about just lspci -n

I can you you dont have a driver assigned to the card with the atheros chipset.  Just trying to figure out which of those two cards it is.

i have the driver for the DWA 542 right off the disk but for the N1 i would have to downlaod it so i was thinking about taking it out and this is what i got with lspci -n

> 
0000:00:00.0 0600: 8086:2770
0000:00:01.0 0604: 8086:2771
0000:00:1b.0 0403: 8086:27d8 (rev 01)
0000:00:1c.0 0604: 8086:27d0 (rev 01)
0000:00:1c.2 0604: 8086:27d4 (rev 01)
0000:00:1c.3 0604: 8086:27d6 (rev 01)
0000:00:1d.0 0c03: 8086:27c8 (rev 01)
0000:00:1d.1 0c03: 8086:27c9 (rev 01)
0000:00:1d.2 0c03: 8086:27ca (rev 01)
0000:00:1d.3 0c03: 8086:27cb (rev 01)
0000:00:1d.7 0c03: 8086:27cc (rev 01)
0000:00:1e.0 0604: 8086:244e (rev e1)
0000:00:1f.0 0601: 8086:27b8 (rev 01)
0000:00:1f.1 0101: 8086:27df (rev 01)
0000:00:1f.2 0101: 8086:27c0 (rev 01)
0000:00:1f.3 0c05: 8086:27da (rev 01)
0000:01:00.0 0300: 1002:5b63
0000:01:00.1 0380: 1002:5b73
0000:02:00.0 0200: 8086:108b (rev 03)
0000:05:02.0 0280: 168c:0023 (rev 01)
0000:05:05.0 0c00: 104c:8024

0000:00:1f.3 0c05: 8086:27da (rev 01)
0000:01:00.0 0300: 1002:5b63
0000:01:00.1 0380: 1002:5b73
0000:02:00.0 0200: 8086:108b (rev 03)
0000:05:02.0 0280: 168c:0023 (rev 01)
0000:05:05.0 0c00: 104c:8024


---

