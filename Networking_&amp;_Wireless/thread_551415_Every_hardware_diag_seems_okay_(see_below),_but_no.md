---
title: "Every hardware diag seems okay (see below), but no way to scan wifi APs ..."
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by Spear on 2007-09-15
Hi !

I own an Allnet Wifi card ; it uses a realtek 8185 chipset ... everything seems to be alright like you see here under, but theres not way to scan any access point around (but Windows does it :().

Thanks for your help :)

Here are the data :

-> dmesg

[   38.451083] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[   38.451086] Copyright (c) 2004-2005, Andrea Merello
[   38.451088] rtl8180: Initializing module
[   38.451090] rtl8180: Wireless extensions version 21
[   38.451092] rtl8180: Initializing proc filesystem
[   38.452288] rtl8180: Configuring chip resources
[   38.452780] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   38.452788] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
[   38.452845] rtl8180: Memory mapped space @ 0xf5000000 
[   38.452865] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[   38.452868] rtl8180: This is a CARDBUS NIC
[   38.452870] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[   38.458912] rtl8180: Card MAC address is 00:18:e7:1a:cc:5d
[   38.473999] rtl8180: EEPROM version 105
[   38.476012] rtl8180: Card reports RF frontend Realtek 8225
[   38.476014] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[   38.476016] rtl8180: WW:use it with care and at your own risk and
[   38.476018] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[   38.476020] rtl8180: Energy threshold: b
[   38.476023] rtl8180: PAPE from CONFIG2: 6
[   38.476153] rtl8180: IRQ 20
[   38.512219] rtl8180: Driver probe completed
[   38.512222] 

-> lspci

01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

-> lsmod

r818x                  89996  0 

-> ifconfig

wlan0     Lien encap:Ethernet  HWaddr 00:18:E7:1A:CC:5D  
          inet adr:192.168.1.18  Bcast:192.255.255.255  Masque:255.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:11088 (10.8 KiB)
          Interruption:20 Mémoire:f891a000-f891a100 

-> iwconfig

wlan0     802.11b/g  Mode:Managed  Frequency=2.467 GHz  
          Access Point: Not-Associated   Bit Rate=11 Mb/s   
          Retry: on   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

-> iwlist scanning

wlan0     No scan results

---

### Post by kevdog on 2007-09-15
Try intstalling ndiswrapper with win98 drivers for your card.  Wireless rtl chipsets are kind of touchy, and the built in driver often does not work.

---

