---
title: "wireless card not working"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by grigri9 on 2007-05-23
I've been using Ubuntu for about a month now and everything been's working really well,  but I've just moved to an apartment where it's only possible to setup a wireless network, and  of course the network card doesn't work (or I just can't get onto the network.) 

Here's the information I saw was asked for in other threads about fixing wireless network problems.


output of lshw -C network

```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:fe8fc000-fe8fffff ioport:9800-98ff irq:10
  *-network DISABLED
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@05:04.0
       logical name: eth0
       version: 14
       serial: 00:18:f3:4a:19:33
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=skge driverversion=1.5 firmware=N/A link=no multicast=yes port=twisted pair
       resources: iomemory:feaf4000-feaf7fff ioport:b800-b8ff irq:225
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:05:e6:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g link..
```


output of lspci

```
0:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation SATA Controller 1 IDE (rev 02)
00:1f.3 SMBus: Intel Corporation SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation SATA Controller 2 IDE (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
```


iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"Dynamo-Home"  
          Mode:Managed  Channel=6  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```




lspci -v | less

```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
        Subsystem: SysKonnect Unknown device 4340
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 9800 [size=256]
        Expansion ROM at fe8c0000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 225
        Memory at feaf4000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at b800 [size=256]
        Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
```

---

### Post by benanzo on 2007-05-24
I might be blind, but I don't actually see a wireless adapter on your PCI bus.  I see that your motherboard has dual gigabit ethernet adapters, is that correct?  What model of motherboard is this?

do this in terminal to update your PCI bus IDs:
```
sudo update-pciids
```

Then rerun the above commands and post them back.

---

### Post by grigri9 on 2007-05-24
running sudo update-pciids doesn't appear to work since I'm not connected to the internet.

I get the following error message.

```
--00:34:06--    http://pciids.sourceforge.net/v2.2/pci.ids.bz2
                 =>  'usr/share/misc/pci.ids.new'
Resolving pciids.sourceforge.net... failed: Temporary failute in name resolution
.
update-pciids: download failed
```

I do have dual gigabit ethernet adapters but I also have a wireless adapter.

The motherboard is and Asus P5B Deluxe w/wifi AP solo

link: [HTML]http://usa.asus.com/products.aspx?l1=3&l2=11&l3=307&l4=0&model=1179&modelmenu=1[/HTML]

---

### Post by grigri9 on 2007-05-24
I've gone through the wireless troubleshooting guide and downloaded ndiswrapper since my card isn't supported under linux. My computer appears to be recognizing my card since I can see it when I go to system->networking I see a wireless interface. However I can't connect to my home router at all. I've tried using dhcp and entering the gateway IP manually but neither of those options works. Any help would be much appreciated.

---

### Post by grigri9 on 2007-05-24
I found a new wireless card and that worked right away after plugging it in. So I'll assume I just have a crappy wireless card that can't see my router from 20 ft away. Does anyone know of any methods I can use to boost the range of my wireless antenna (copper wire, aluminum foil etc.)?

---

