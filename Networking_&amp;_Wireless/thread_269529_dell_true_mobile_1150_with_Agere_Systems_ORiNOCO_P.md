---
title: "dell true mobile 1150 with Agere Systems ORiNOCO PCI Adapter"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by supergumby on 2006-10-01
Hi Folks,

I want to configure my dell truemobile 1150 wireless card with my Agere Systems ORiNOCO PCI Adapter in my desktop system. I know the wireless card is working fine with ubuntu since I use it also on my laptop sometimes, no problem at all. But I can't find any info about how to make this PCI adaptor work with my wireless card. I'm pretty new to ubuntu so let me know if you know something else from me. Here is the lspci -v partial output:

0000:00:0a.0 Network controller: Agere Systems ORiNOCO PCI Adapter
        Subsystem: Agere Systems ORiNOCO PCI Adapter
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 6c00 [size=128]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:50:BA:50:13:8E
          inet addr:104.40.145.118  Bcast:104.40.145.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe50:138e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4242 errors:111 dropped:0 overruns:0 frame:0
          TX packets:4087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3916024 (3.7 MiB)  TX bytes:780574 (762.2 KiB)
          Interrupt:5 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4120 (4.0 KiB)  TX bytes:4120 (4.0 KiB)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

lshw (partial)

  *-network:1 UNCLAIMED
             description: Network controller
             product: ORiNOCO PCI Adapter
             vendor: Agere Systems
             physical id: a
             bus info: pci@00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: ioport:6c00-6c7f irq:10

---

