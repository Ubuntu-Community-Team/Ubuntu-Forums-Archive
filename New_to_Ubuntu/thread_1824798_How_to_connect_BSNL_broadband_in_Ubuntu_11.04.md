---
title: "How to connect BSNL broadband in Ubuntu 11.04?"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by LavenderBlack on 2011-08-14
Hi all,
My laptop is Toshiba Satellite L640. I was initially using ubuntu 10.10,  in which i configured bsnl broadband as a dsl connection and configured the port using "sudo pppoeconf" command. It was working fine. Few days back I upgraded to 11.04 and net got disconnected after that. I am unable to configure and connect as before.  Here are some outputs that could be useful. Can someone help me on this???


> 
lavender@lavender-Satellite-L640:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:e8:b0:71  
          inet6 addr: fe80::ca0a:a9ff:fee8:b071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:22396 (22.3 KB)  TX bytes:24693 (24.6 KB)
          Interrupt:42 

eth1      Link encap:Ethernet  HWaddr e8:39:df:3e:ae:a2  
          inet6 addr: fe80::ea39:dfff:fe3e:aea2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8366 (8.3 KB)  TX bytes:8366 (8.3 KB)

> 
lavender@lavender-Satellite-L640:~$ plog
Aug 14 17:56:11 lavender-Satellite-L640 pppd[2208]: Using interface ppp0
Aug 14 17:56:11 lavender-Satellite-L640 pppd[2208]: Connect: ppp0 <--> eth0
Aug 14 17:56:12 lavender-Satellite-L640 pppd[2208]: CHAP authentication failed: User not found
Aug 14 17:56:12 lavender-Satellite-L640 pppd[2208]: CHAP authentication failed
Aug 14 17:56:12 lavender-Satellite-L640 pppd[2208]: Connection terminated.
Aug 14 17:56:12 lavender-Satellite-L640 pppd[2208]: Exit.

> 
lavender@lavender-Satellite-L640:~$ ifconfig ppp0
ppp0: error fetching interface information: Device not found


---

### Post by westie457 on 2011-08-14
> **LavenderBlack said:**
> Hi all,
My laptop is Toshiba Satellite L640. I was initially using ubuntu 10.10,  in which i configured bsnl broadband as a dsl connection and configured the port using "sudo pppoeconf" command. It was working fine. Few days back I upgraded to 11.04 and net got disconnected after that. I am unable to configure and connect as before.  Here are some outputs that could be useful. Can someone help me on this???

Hello.

Open a terminal and run ```
lspci -vnn

lshw -C network

iwconfig

rfkill list all
```

Select all the output and hit new reply or quote and the # at the top of the message window paste between [CODE] tags

Thank you.

---

### Post by LavenderBlack on 2011-08-14
> **westie457 said:**
> Hello.

Open a terminal and run ```
lspci -vnn

lshw -C network

iwconfig

rfkill list all
```Select all the output and hit new reply or quote and the # at the top of the message window paste between ```
 tags

Thank you.

Hi westie,
             
[CODE]
lavender@lavender-Satellite-L640:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Core  Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if  00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5080 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at 96405900 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series  Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05) (prog-if 20  [EHCI])
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 96405400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at 96400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series  Chipset PCI Express Root Port 1 [8086:3b42] (rev 05) (prog-if 00 [Normal  decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 95400000-963fffff
    Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series  Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05) (prog-if 00 [Normal  decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 94400000-953fffff
    Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series  Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05) (prog-if 00 [Normal  decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 93400000-943fffff
    Prefetchable memory behind bridge: 0000000092400000-00000000933fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series  Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05) (prog-if 20  [EHCI])
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at 96405000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series  Chipset 4 port SATA IDE Controller [8086:3b28] (rev 05) (prog-if 8f  [Master SecP SecO PriP PriO])
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 5078 [size=8]
    I/O ports at 5094 [size=4]
    I/O ports at 5070 [size=8]
    I/O ports at 5090 [size=4]
    I/O ports at 5050 [size=16]
    I/O ports at 5040 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: medium devsel, IRQ 10
    Memory at 96405800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series  Chipset 2 port SATA IDE Controller [8086:3b2d] (rev 05) (prog-if 85  [Master SecO PriO])
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 5068 [size=8]
    I/O ports at 508c [size=4]
    I/O ports at 5060 [size=8]
    I/O ports at 5088 [size=4]
    I/O ports at 5030 [size=16]
    I/O ports at 5020 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.6 Signal processing controller [1180]: Intel Corporation 5  Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at 96404000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7175]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, brcm80211

03:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at 93400000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath  Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Flags: bus master, fast devsel, latency 0


``````

lavender@lavender-Satellite-L640:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: e8:39:df:3e:ae:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:94400000-94403fff
  *-network
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: c8:0a:a9:e8:b0:71
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 link=yes  multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:93400000-9343ffff ioport:2000(size=128)
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 02:80:37:0e:03:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether  driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=no  multicast=yes


``````
lavender@lavender-Satellite-L640:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:245
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

usb0      no wireless extensions.

ppp1      no wireless extensions.

``````
lavender@lavender-Satellite-L640:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by dineshs on 2011-08-17
1)Are you using wired?wireless? or both?Can you post the ourput of ```
sudo dhclient eth0
``` when ethernet cable is connected.
pppoeconf command is used when your modem is in bridge mode.It is always better to configure the modem in pppoe mode for an always ON connection
Ref:[http://www.syncnext.com/bsnl/broadband/bridge-vs-pppoe-modem-mode-bsnl-broadband/105.html](http://www.syncnext.com/bsnl/broadband/bridge-vs-pppoe-modem-mode-bsnl-broadband/105.html)

---

