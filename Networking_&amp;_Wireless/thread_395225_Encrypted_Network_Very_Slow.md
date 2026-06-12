---
title: "Encrypted Network Very Slow"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by HeelsFan on 2007-03-27
I have a Thinkpad R31 with Ubuntu 6.10 installed.  I am using a Linksys WPC11 ver.3 wireless card to connect to the network through a Linksys WRT54GS wireless router.

When I am plugged into the router directly or when I am using wireless without encryption, I can connect to the network with no problem and I can browse the internet with pretty good speeds.

However, when I encrypt (both 64 and 128 bit) I connect to the network, but internet browsing is extremely slow as loading pages can take over two minutes to come up with anything and rarely finish loading.

I can connect to the encrypted network fine with my WinXP laptop and have good browsing speeds on the internet.  I can also connect to other unencrypted networks in my neighborhood with good speed.

I tried disabling IPV6 in Firefox and in the /etc/modprobe.d/aliases, but this had no affect.

The only thing I can think of now is driver issues with the wireless card.  Does anyone have any suggestions or other tips?

Thanks in advance from a noob.

---

### Post by chili555 on 2007-03-27
I'd also try /etc/modprobe.d/blacklist. Add:```
blacklist  ipv6
```Please reboot and post back.

---

### Post by HeelsFan on 2007-03-28
Thanks for the suggestion, but unfortunately that had no affect either.

---

### Post by chili555 on 2007-03-28
May we please see:```
lspci -v | grep Network
lsmod | grep prism
```Thanks.

---

### Post by HeelsFan on 2007-03-28
I'm definitely showing my noobness, but when I run those in terminal nothing happens.  I just copied and pasted the requested lines of text into terminal, hit enter, and nothing happened.  Usually when I do iwconfig or something of the sort in terminal I see text come up, but nothing in this case.

---

### Post by chili555 on 2007-03-28
That just means, "I have nothing to report." Let's try harder. Let's see ```
lspci -v
```We'll get it.

---

### Post by HeelsFan on 2007-04-05
Finally got some time to get back to this after a crazy week at work and of course all the time my 6 month old daughter takes up when I finally get home from work.

Here's the output:

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
        Subsystem: IBM Unknown device 1017
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04) (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 0505
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at 98000000 (32-bit, prefetchable) [size=128M]
        Memory at 90100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
        Subsystem: IBM Unknown device 0505
        Flags: bus master, fast devsel, latency 0
        Memory at 88000000 (32-bit, prefetchable) [size=128M]
        Memory at 80200000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 1017
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at a4a0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 1017
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at a4e0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 1017
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at a800 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=05, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: 80100000-801fffff
        Prefetchable memory behind bridge: 20000000-21ffffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM Unknown device 1017
        Flags: bus master, medium devsel, latency 0, IRQ 255
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at a890 [size=16]
        Memory at 22000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
        Subsystem: IBM Unknown device 1017
        Flags: medium devsel, IRQ 11
        I/O ports at 8000 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: IBM Unknown device 0500
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 9800 [size=256]
        I/O ports at 9c00 [size=64]

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: IBM ThinkPad R31 2656BBG
        Flags: medium devsel, IRQ 11
        I/O ports at a000 [size=256]
        I/O ports at a400 [size=128]

01:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
        Subsystem: IBM Unknown device 1031
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at 80100000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 7000 [size=64]
        Capabilities: <access denied>

01:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
        Subsystem: IBM Unknown device 1017
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 80101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 24000000-25fff000
        I/O window 0: 00007400-000074ff
        I/O window 1: 00007800-000078ff
        16-bit legacy interface ports at 0001

Thanks!

---

### Post by HeelsFan on 2007-04-10
I'm not a huge fan of bumps, but I'm still having problems with this and would appreciate any help anyone can provide.

Thanks in advance.

---

### Post by chili555 on 2007-04-11
Wonderful! lspci has confirmed nothing about your card! With the card inserted, please do the following commands:```
sudo lshw -C network
lsmod | grep orinoco
lsmod | grep hostap
```Remember, the cursor will pop back to the prompt is there is nothing to report, which is itself, valuable information.

---

### Post by HeelsFan on 2007-05-25
Output from lshw -C network:

  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 42
       serial: 00:00:e2:6d:1c:78
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:80100000-80100fff ioport:7000-703f irq:11
  *-network
       description: Instant Wireless Network PC Card
       product: ISL37300P
       vendor: The Linksys Group, Inc.
       physical id: 0
       version: RevA
       slot: Socket 0
       resources: irq:5
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:06:25:ab:64:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.4 ip=192.168.1.106 link=yes multicast=yes wireless=IEEE 802.11b

Output from lsmod | grep orinoco:

orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 39212  2 hostap_cs,orinoco_cs
pcmcia_core            40852  5 hostap_cs,orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

Output from lsmod | grep hostap:

hostap_cs              62740  0 
hostap                113924  1 hostap_cs
ieee80211_crypt         7040  1 hostap
pcmcia                 39212  2 hostap_cs,orinoco_cs
pcmcia_core            40852  5 hostap_cs,orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

Thanks!

---

