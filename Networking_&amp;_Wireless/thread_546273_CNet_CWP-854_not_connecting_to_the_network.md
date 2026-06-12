---
title: "CNet CWP-854 not connecting to the network"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by tph on 2007-09-08
Today my dad purchased a CNet CWP-854 wireless pci-card today so that he wouldn't have to be dependent on wires all the time to stay online.
I inserted it in a pci-slot and booted the computer, and everything seemed fine. Ubuntu recognise the card and I can search for networks etc. but when I try to connect to the wireless network, it tries to connect for maybe a minute or two, then it fails.
The wiki says that the card work out of the box in feisty (he is running feisty), and it does until I try to connect to a network.
Furthermore, when I booted up Windows XP and tried to connect, it all went fine even though it took a while to connect.

I've tried to search around, but I haven't managed to find a similar problem, and a solution to it yet.

**Edit:** It seems that the wiki had all the answers I was looking for at [https://wiki.ubuntu.com/Rt61WirelessCardsHowTo#head-266b523ecf4285410a28edba1ef42a082f7f2439](https://wiki.ubuntu.com/Rt61WirelessCardsHowTo#head-266b523ecf4285410a28edba1ef42a082f7f2439)

---

### Post by noob12 on 2007-09-09
Can you post the output from these commands
```

lspci -nn

sudo lshw -C network

sudo iwlist scan

iwconfig

```

---

### Post by tph on 2007-09-15
Sorry for not answering, I've been quite busy. I haven't gotten the pc to connect on ubuntu yet.

Here's the output form the commands
lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 [8086:2664] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:00.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]
06:01.0 Modem [0703]: Smart Link Ltd. SmartLink SmartPCI562 56K Modem [163c:3052] (rev 04)
06:05.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 61)
06:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 03)
```

sudo lshw -C network
```
  *-network:0
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 0
       bus info: pci@06:00.0
       logical name: ra0
       version: 00
       serial: 00:08:a1:b5:aa:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=32 link=yes multicast=yes wireless=RT61 Wireless
       resources: iomemory:ff8f8000-ff8fffff irq:23
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@06:08.0
       logical name: eth0
       version: 03
       serial: 00:11:11:78:2c:3e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.0.101 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:ff8f5000-ff8f5fff ioport:bc00-bc3f irq:22
```

sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:1B:11:E4:EF:19
                    ESSID:"TaylorByeID"
                    Mode:Managed
                    Channel:11
                    Encryption key:off
                    Quality:75/100  Signal level:-59 dBm  Noise level:-256 dBm

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"TaylorByeID"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:11:E4:EF:19   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=79/100  Signal level:-60 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

In case anyone wonders, I haven't encrypted the network because Nintendo DS can't handle WPA and WEP doesn't really help at all. I've filtered mac-addresses though (yes, I did add the mac-address of the wireless card), and there are plenty open wireless networks in the neighbourhood.

Anyways, I hope anyone can help me.

---

