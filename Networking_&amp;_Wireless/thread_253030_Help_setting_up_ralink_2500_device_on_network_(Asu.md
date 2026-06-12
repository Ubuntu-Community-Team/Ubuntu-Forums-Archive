---
title: "Help setting up ralink 2500 device on network (Asus WL107G). Terminal output below."
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by alanmzifa on 2006-09-07
Hi, I'm pretty new to Linux. Just trying to add a new (old) laptop to my router with a Asus WL107G PCMCIA card (ralink2500 chipset).

Have spent about 3 to 4 hours tinkering so far but no real change.
[I]
I think the kernel sees the device.
I think the device sees the router and the driver.
I can't see the IP for the device but sometimes there seems to one assigned in network settings.????[/I]

To speed things along here's some output.

iwconfig

> 
ra0       RT2500 Wireless  ESSID:"W office"
          Mode:Managed  Frequency=2.447 GHz  Access Point: 00:09:5B:CD:08:38          Bit Rate:11 Mb/s   Tx-Power:1 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=56/100  Signal level=-84 dBm  Noise level:-202 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lshw
> 
q:10
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:24120000-24120fff irq:10
        *-network
             description: Ethernet interface
             product: 3c905C-TX/TX-M [Tornado]
             vendor: 3Com Corporation
             physical id: d
             bus info: pci@00:0d.0
             logical name: eth2
             version: 78
             serial: 00:06:5b:30:bc:3b
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=3c59x ip=192.168.1.11 multicast=yes
             resources: ioport:fc00-fc7f iomemory:fededc00-fededc7f irq:10
        *-communication UNCLAIMED
             description: Communication controller
             product: WinModem 56k
             vendor: Agere Systems
             physical id: 10
             bus info: pci@00:10.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:feded800-feded8ff ioport:fcc8-fccf ioport:f800-f8ff irq:3
     *-network
          description: Wireless interface
          product: Ralink RT2500 802.11 Cardbus Reference Card
          vendor: RaLink
          physical id: 0
          bus info: pci@02:00.0
          logical name: ra0
          version: 01
          serial: 00:17:31:9c:8c:8d
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=rt2500 multicast=yes wireless=RT2500 Wireless
          resources: iomemory:22000000-22001fff irq:10

ifconfig

> ra0       Link encap:Ethernet  HWaddr 00:17:31:9C:8C:8D
          inet6 addr: fe80::217:31ff:fe9c:8c8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4220 errors:111 dropped:111 overruns:0 carrier:0
          collisions:39 txqueuelen:1000
          RX bytes:9073 (8.8 KiB)  TX bytes:210410 (205.4 KiB)
          Interrupt:10 Base address:0x8000

---

### Post by alanmzifa on 2006-09-08
I still haven't been able to crack this, but I imagine it's probably something simple as some of the bricks seem to be in place. 

Any help would be appreciated. 

Thanks

---

### Post by alanmzifa on 2006-09-08
ok

not getting better. getting worse.

as no takers on this thread tried to work things out from what I read.

removed wifi-radar.
installed network manager.
blocked ipv6
took down software firewall
allowed range of Ip addresses to come in on router firewall

currently .....


now don't have any connection, wired ethernet or wireless.
when I did have what looked like a wireless internet connection no web pages loaded.


can someone please lend a hand, make some suggestions, take a look at some output?

---

### Post by alanmzifa on 2006-09-09
just a polite bump

---

### Post by alanmzifa on 2006-09-13
With the help of the networking forum I have been able to get my PCMCIA card working.


Here is some additional info others may find useful if using this card in the future.

Device      *Asus WL107G PCMCIA wireless card*
Software    *Ubuntu 6.06 standard unmodified 2.6.15-26-386 kernel*
Software    *Network Manager installed*
Security    *WEP, 128 bit, hexadecimal, open.*
Connection  *used static connection rather than DHCP*
Driver      *driver is already pre-installed in Ubuntu 6.06, Ralink 2500*

---

