---
title: "Network Card not found"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by Michelexub on 2008-11-09
Hi.
I have installed Xubuntu Intrepid 8.10 on Laptop Acer Aspire 1312.
I use a PCMCIA NETGEAR WIRELESS CARD WG511 (v1).

Before I had Xubuntu 8.04 and with ndiswrapper (and a lot of help) I managed to get the wireless working.

Since I did a cleaned install, all my configurations went lost.

Now my laptop does not even detect the card.
Here the output of few commands:

**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

**lspci:**
00:00.0 Host bridge: VIA Technologies, Inc. P/KN266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
02:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

**sudo lshw -C network:**
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:22:2d:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.2 latency=128 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 8
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:ce:c8:de:4c:64
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

If anyone has any idea I'll be grateful.
Thanks,
Michele

---

### Post by Michelexub on 2008-11-18
Has anyone got some suggestion?

Michele

---

### Post by Michelexub on 2008-11-22
Finally I have solved my problem!!!

I had to blacklist prism54, then to download windows drivers.
Boot into windows and extract .sys and .inf.
Then in Xubuntu I used ndiswrapper to install them.

Michele

---

