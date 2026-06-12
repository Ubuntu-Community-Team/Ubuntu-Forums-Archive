---
title: "Linksys 802.11g card compatability problems"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by ghettosamson on 2007-12-28
So, I've successfully installed gusty 64bit on my laptop, and gotten skype and the works running on it. Now Ive installed gutsy standard version on my desktop. I installed it at my friends computer graveyard house, where he has a wirelesss-g network. I successfully connect to his network no problem. I have the linksys wireless-g pci card. Now, I bring it home, where my roommate has a wireless-b network and the problems start happening. I get good signal strength and it connects to the network, but i cant get internet access. So I took it down stairs, hooked it up thru cat5 and i'm connected. Unplugged the cat5, and the wireless worked. Restarted the computer and no more internet access. So im using xp until i solve this problem cuz i dont have any problems in xp.
iwconfig results
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"RedDevils"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:4E:81:4F   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

well now it is working. not any more. Whats going on?

---

### Post by Kobalt on 2007-12-28
What kind of card is yours (you can find some useful information using the command line *lspci*)? How did you install it? 
My guess is wether it's a driver problem that makes your card connect randomly or it's a configuration issue (such as DHCP, encryption key, etc.) with your network. 

Please give us some more info about that.

---

### Post by ghettosamson on 2008-01-05
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

That is the output from lspci. I installed it when the computer was powered off and I had only xp on it. Then when I installed ubuntu it automatically read the device. My netwrok is protected by a 64 bit hex wep. Hope that helps.

---

