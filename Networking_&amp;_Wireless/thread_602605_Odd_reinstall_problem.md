---
title: "Odd reinstall problem"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by FighterOfTheNightMan on 2007-11-04
Hey,

I had Ubuntu 7.10 installed with a Linksys Wireless G pci adapter.  Everything worked great, it recognized it and worked RIGHT AWAY.  No configuration was needed.  I got a new computer, downloaded the 64-bit version of Gutsy Gibbon, installed it and it does not work.  The activity light comes on, but no one is home.

I've tried different PCI slots (I have 3), tried installing Gutsy with and without the adapter installed.  Nothing seems to make a difference.  It all results in the activity light on, solid green light, but it not working.  I have a Cantenna which is in the same position as it was before the reinstall, so I don't think it has anything to do with it not getting a signal.  

This may or may not be related, but this card doesn't register with Windows.  It did a while ago, but then installed Gutsy and it didn't work after that.  Kind of weird.  Any input is appreciated.

Regards,

Brandon


edit:  Here is the output of lspci

elwood@elwood-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
elwood@elwood-desktop:~$ 

Second edit:  For kicks and giggles, here is iwconfig:

elwood@elwood-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

