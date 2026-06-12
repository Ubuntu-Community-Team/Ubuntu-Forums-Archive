---
title: "USR2410 Card and wlan-ng problems"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by theShogun on 2007-03-18
I recently installed Edgy on a laptop. During the install I had a U.S. Robotics PCMCIA card  (USR2410) inserted. The card was not detected or activated during install, and now I can't seem to get this card to run. I have dug through the forums and put google to work but all to no avail. I've tried several different linux-wlan-ng installs, different ndiswrapper .inf's,  and sketchy modprobes with no results. 

The output of lspci is 

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)

```

and iwconfig gives

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  Nickname:"Prism  I"
          Mode:Managed  
          RTS thr:off   
          Link Quality:0  Signal level:134  Noise level:134
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sit0      no wireless extensions.

```

From what I've seen in the forums, this card should work. What am I missing? Any help or points in the right direction would be appreciated.

---

### Post by theShogun on 2007-03-19
Update: I took the cheater's way out and installed Dapper. Dapper auto-detected the card and set me right up.

---

