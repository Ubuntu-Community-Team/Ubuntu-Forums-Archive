---
title: "NetworkManager Applet Quirks after Latest Upgrade"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by mejohnsn on 2009-09-19
Synaptic Package Manager says I have 0.1.7~rc4.1.cf199a964-0ubuntu2 installed.

But when I right-click on the NetworkManager icon in the top bar/tray and select 'About', it says I have 0.7.0.100.

Why this discrepancy? Even more important, why does it, ever since the update via Update Manager yesterday, always claim there are no Wireless Connections? There actually is a connection, I can run Firefox and reach the Internet, but NetworkManager insists I have no Wireless Connections to view, select, or edit (or any other connections).

Yet here I am posting from the very machine it claims has no connections!

I am running Ubuntu 9.04, I ran the update manager yesterday to get all the latest (I have Software Sources set to allow all but pre-release and unsupported).

BTW: ifconfig can find wlan0 with no problems, it even shows the right ESSID for the active connection NetworkManager cannot see.

I have to wonder, though, about the lspci output: I cannot recognize wlan0 in that output:

```

lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
00:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
06:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

```

I thought 12.0 was the Ethernet controller for a wired connection. Then again, the last line says 802.11g, so perhaps that is the device being used for wlan0. But then why doesn't it recoginze 802.11b capabilities?

---

