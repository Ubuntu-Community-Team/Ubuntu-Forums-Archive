---
title: "Ubuntu 12.04LTS Time Warner Wifi Issue"
date: 2014-08-05
forum: Networking &amp; Wireless
---

### Post by josh72 on 2014-08-05
Hello,

I just setup a new wireless network, and I'm unable to connect when running ubuntu (no issues when using windows 7, or connecting to other public wireless networks with ubuntu). I also have no problem connecting directly to the modem by ethernet cable. I'm relatively inexperienced with linux, so any advice as to how to fix this problem through terminal commands will have to be fairly thorough; I'm unsure of where to begin.
Thanks in advance,
Josh

Edit: I ran
 ```
 
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script 
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
and the returned output is attached.[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]


[/FONT][/COLOR]

---

### Post by josh72 on 2014-08-06
I've pasted the tar file below..any help would be appreciated.

---

### Post by josh72 on 2014-08-06
```



########## wireless info START ##########


Report from: 05 Aug 2014 21:47 EDT -0400


Script from: 04 Aug 2014 18:47 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise


##### kernel #####


Linux 3.5.0-37-generic #58~precise1-Ubuntu SMP Wed Jul 10 17:51:56 UTC 2013 i686 i686 i386 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


05:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak] [8086:0087] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN [8086:1321]
	Kernel driver in use: iwlwifi


0b:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Dell Device [1028:02fe]
	Kernel driver in use: tg3


##### lsusb #####


Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:640f Microdia 
Bus 002 Device 012: ID 8086:0188 Intel Corp. WiMAX Connection 2400m
Bus 002 Device 013: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 014: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 015: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 002 Device 016: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card


##### PCMCIA Card Info #####


##### rfkill #####


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: i2400m-usb:2-1.5:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


dell_wmi               12602  0 
sparse_keymap          13659  1 dell_wmi
wmi                    18745  1 dell_wmi
iwlwifi               364652  0 
mac80211              475546  1 iwlwifi
cfg80211              181041  2 iwlwifi,mac80211


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:474615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:710597561 (710.5 MB)  TX bytes:13968024 (13.9 MB)
          Interrupt:17 


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wmx0      Link encap:Ethernet  HWaddr <MAC addr wmx0>  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig #####


wmx0      no wireless extensions.


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connecting


- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr wmx0>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         off


- Device: wlan0  [DDW36503] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC addr wlan0>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Ny state of mind ext1: Infra, <MAC addr Clarity_Connect_407>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    Kingsbury Arch:  Infra, <MAC addr 001244b56fb0>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Clarity_Connect_407: Infra, <MAC addr DDW361150>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    001244b56fb0:    Infra, <MAC addr MKZ>, Freq 2452 MHz, Rate 54 Mb/s, Strength 89 WEP
    DDW361150:       Infra, <MAC addr DDW36503>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    MKZ:             Infra, <MAC addr HARDY_EXT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    DDW36503:        Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    NY State of Mind:Infra, <MAC address>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    HARDY_EXT:       Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels #####


wmx0      no frequency information.


lo        no frequency information.


eth0      no frequency information.


wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz


##### iwlist scan #####


wmx0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr DDW361150>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Clarity_Connect_407"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000558f5a95c7
                    Extra: Last beacon: 48ms ago
          Cell 02 - Address: <MAC addr 001244b56fb0>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Kingsbury Arch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004c0f01ee183
                    Extra: Last beacon: 3176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr MKZ>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"001244b56fb0"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000054df5da5c93
                    Extra: Last beacon: 3088ms ago
          Cell 04 - Address: <MAC addr Clarity_Connect_407>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Ny state of mind ext1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000001e4570
                    Extra: Last beacon: 3120ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr DDW36503>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"DDW361150"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002818d9a4de
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"DDW36503"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002dfbfb5db
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HARDY_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014a6c484ae1
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos #####


[iwlwifi]
filename:       /lib/modules/3.5.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     5B371950CE3735654DCD689
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.5.0-37-generic SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)


##### module parameters #####


[iwlwifi]
11n_disable: 0
5ghz_disable: N
amsdu_size_8K: 1
antenna_coupling: 0
auto_agg: Y
bt_ch_inhibition: Y
bt_coex_active: Y
fw_restart: 1
led_mode: 0
plcp_check: Y
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 0


##### /etc/modules #####


lp


##### blacklists #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### udev rules #####


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:0b:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   14.779834] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.779840] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   14.779978] iwlwifi 0000:05:00.0: pci_resource_len = 0x00002000
[   14.779983] iwlwifi 0000:05:00.0: pci_resource_base = f84e0000
[   14.779988] iwlwifi 0000:05:00.0: HW Revision ID = 0x35
[   14.780126] iwlwifi 0000:05:00.0: irq 46 for MSI/MSI-X
[   14.809224] type=1400 audit(1407285584.540:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
[   15.006969] iwlwifi 0000:05:00.0: loaded firmware version 41.28.5.1 build 33926
[   15.007171] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   15.007174] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   15.007176] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   15.007179] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   15.007181] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_P2P disabled
[   15.007184] iwlwifi 0000:05:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[   15.007321] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[   15.007506] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[   15.018452] iwlwifi 0000:05:00.0: device EEPROM VER=0x536, CALIB=0x6
[   15.018455] iwlwifi 0000:05:00.0: Device SKU: 0x1F0
[   15.018456] iwlwifi 0000:05:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[   15.018471] iwlwifi 0000:05:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.021654] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.673510] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[   15.674056] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[   15.924426] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[   15.924625] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[   16.047532] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.048708] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.456449] i2400m_usb 2-1.5:1.0: firmware interface version 9.3.2
[   45.323281] wlan0: authenticate with <MAC address>
[   45.330070] wlan0: direct probe to <MAC address> (try 1/3)
[   45.533394] wlan0: direct probe to <MAC address> (try 2/3)
[   45.737255] wlan0: direct probe to <MAC address> (try 3/3)
[   45.941060] wlan0: authentication with <MAC address> timed out
[   76.597832] wlan0: authenticate with <MAC address>
[   76.599492] wlan0: direct probe to <MAC address> (try 1/3)
[   76.801707] wlan0: direct probe to <MAC address> (try 2/3)
[   77.005708] wlan0: direct probe to <MAC address> (try 3/3)
[   77.209436] wlan0: authentication with <MAC address> timed out
[   85.430455] wlan0: authenticate with <MAC address>
[   85.433022] wlan0: direct probe to <MAC address> (try 1/3)
[   85.633884] wlan0: direct probe to <MAC address> (try 2/3)
[   85.837710] wlan0: direct probe to <MAC address> (try 3/3)
[   86.041702] wlan0: authentication with <MAC address> timed out
[   94.229467] wlan0: authenticate with <MAC address>
[   94.241008] wlan0: direct probe to <MAC address> (try 1/3)
[   94.442175] wlan0: direct probe to <MAC address> (try 2/3)
[   94.645999] wlan0: direct probe to <MAC address> (try 3/3)
[   94.849817] wlan0: authentication with <MAC address> timed out
[  215.985848] wlan0: authenticate with <MAC address>
[  215.987713] wlan0: send auth to <MAC address> (try 1/3)
[  216.190426] wlan0: send auth to <MAC address> (try 2/3)
[  216.394232] wlan0: send auth to <MAC address> (try 3/3)
[  216.598172] wlan0: authentication with <MAC address> timed out
[  259.649783] wlan0: authenticate with <MAC address>
[  259.652576] wlan0: direct probe to <MAC address> (try 1/3)
[  259.855915] wlan0: direct probe to <MAC address> (try 2/3)
[  260.059593] wlan0: direct probe to <MAC address> (try 3/3)
[  260.263428] wlan0: authentication with <MAC address> timed out
[  470.670317] wlan0: authenticate with <MAC address>
[  470.672850] wlan0: direct probe to <MAC address> (try 1/3)
[  470.873136] wlan0: direct probe to <MAC address> (try 2/3)
[  471.077125] wlan0: direct probe to <MAC address> (try 3/3)
[  471.280814] wlan0: authentication with <MAC address> timed out
[  638.505299] wlan0: authenticate with <MAC address>
[  638.508894] wlan0: direct probe to <MAC address> (try 1/3)
[  638.712641] wlan0: direct probe to <MAC address> (try 2/3)
[  638.916536] wlan0: direct probe to <MAC address> (try 3/3)
[  639.120283] wlan0: authentication with <MAC address> timed out
[  647.362298] wlan0: authenticate with <MAC address>
[  647.365158] wlan0: direct probe to <MAC address> (try 1/3)
[  647.568812] wlan0: direct probe to <MAC address> (try 2/3)
[  647.772641] wlan0: direct probe to <MAC address> (try 3/3)
[  647.976472] wlan0: authentication with <MAC address> timed out
[  725.480375] wlan0: authenticate with <MAC address>
[  725.482042] wlan0: send auth to <MAC address> (try 1/3)
[  725.683787] wlan0: send auth to <MAC address> (try 2/3)
[  725.887689] wlan0: send auth to <MAC address> (try 3/3)
[  726.091436] wlan0: authentication with <MAC address> timed out
[ 1089.561021] wlan0: authenticate with <MAC address>
[ 1089.563442] wlan0: direct probe to <MAC address> (try 1/3)
[ 1089.764942] wlan0: direct probe to <MAC address> (try 2/3)
[ 1089.968873] wlan0: direct probe to <MAC address> (try 3/3)
[ 1090.172732] wlan0: authentication with <MAC address> timed out
[ 1453.389616] wlan0: authenticate with <MAC address>
[ 1453.392156] wlan0: direct probe to <MAC address> (try 1/3)
[ 1453.595373] wlan0: direct probe to <MAC address> (try 2/3)
[ 1453.799108] wlan0: direct probe to <MAC address> (try 3/3)
[ 1454.002913] wlan0: authentication with <MAC address> timed out
[ 1816.993555] wlan0: authenticate with <MAC address>
[ 1816.996506] wlan0: direct probe to <MAC address> (try 1/3)
[ 1817.197655] wlan0: direct probe to <MAC address> (try 2/3)
[ 1817.401668] wlan0: direct probe to <MAC address> (try 3/3)
[ 1817.605362] wlan0: authentication with <MAC address> timed out
[ 2163.991183] iwlwifi 0000:05:00.0: RF_KILL bit toggled to disable radio.
[ 2163.994902] iwlwifi 0000:05:00.0: Not sending command - RF KILL
[ 2772.719720] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2839.887335] type=1400 audit(1407288411.845:37): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9134 comm="apparmor_parser"
[ 3048.075582] type=1400 audit(1407288620.217:53): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=11446 comm="apparmor_parser"
[ 3381.569091] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[ 3381.686881] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[ 3381.687085] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[ 3381.825737] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3390.581017] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3396.617371] wlan0: authenticate with <MAC address>
[ 3396.622628] wlan0: send auth to <MAC address> (try 1/3)
[ 3396.824308] wlan0: send auth to <MAC address> (try 2/3)
[ 3397.028223] wlan0: send auth to <MAC address> (try 3/3)
[ 3397.231969] wlan0: authentication with <MAC address> timed out
[ 3405.385916] wlan0: authenticate with <MAC address>
[ 3405.388865] wlan0: direct probe to <MAC address> (try 1/3)
[ 3405.592632] wlan0: direct probe to <MAC address> (try 2/3)
[ 3405.796456] wlan0: direct probe to <MAC address> (try 3/3)
[ 3406.000260] wlan0: authentication with <MAC address> timed out
[ 3463.727532] wlan0: authenticate with <MAC address>
[ 3463.729115] wlan0: send auth to <MAC address> (try 1/3)
[ 3463.932973] wlan0: send auth to <MAC address> (try 2/3)
[ 3464.136836] wlan0: send auth to <MAC address> (try 3/3)
[ 3464.340618] wlan0: authentication with <MAC address> timed out
[ 3619.663750] iwlwifi 0000:05:00.0: RF_KILL bit toggled to disable radio.
[ 3619.803085] iwlwifi 0000:05:00.0: Not sending command - RF KILL
[ 3626.172134] i2400m_usb 2-1.5:1.0: firmware interface version 9.3.2
[ 4008.982929] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[ 4008.994835] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[ 4008.995036] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[ 4009.133312] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4037.283096] wlan0: authenticate with <MAC address>
[ 4037.290490] wlan0: direct probe to <MAC address> (try 1/3)
[ 4037.492197] wlan0: direct probe to <MAC address> (try 2/3)
[ 4037.696149] wlan0: direct probe to <MAC address> (try 3/3)
[ 4037.899813] wlan0: authentication with <MAC address> timed out


########## wireless info END ############

```

---

### Post by jeremy31 on 2014-08-06
I would run this in terminal first as your kernel isn't the latest
```
[COLOR=#000000]sudo apt-get update
```[/COLOR]
[COLOR=#000000]```
sudo apt-get upgrade
```

And see if the updates help you[/COLOR]

---

### Post by josh72 on 2014-08-06
I Updated and the problem wasn't fixed

---

### Post by josh72 on 2014-08-08
Does anyone have any other suggestions? I've tried just about everything I can think of over the past few days with no luck.

---

### Post by jeremy31 on 2014-08-08
Have you tried Ubuntu 14.04?

---

### Post by josh72 on 2014-08-08
I upgraded to 14.04.1, and the problem isn't fixed. I'd really prefer to not have to go back to using windows, and I'm sure there's a solution somewhere. Anything else I could try? I reran the wireless script and posted the output below.

---

### Post by josh72 on 2014-08-08
```


########## wireless info START ##########

Report from: 08 Aug 2014 18:32 EDT -0400

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash

##### desktop #####

Ubuntu

##### lspci #####

05:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak] [8086:0087] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN [8086:1321]
    Kernel driver in use: iwlwifi

0b:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Dell Device [1028:02fe]
    Kernel driver in use: tg3

##### lsusb #####

Bus 002 Device 012: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 002 Device 011: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 002 Device 010: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 009: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 008: ID 8086:0188 Intel Corp. WiMAX Connection 2400m
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:640f Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: i2400m-usb:2-1.5:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

iwldvm                214950  0 
dell_wmi               12665  0 
mac80211              546051  1 iwldvm
sparse_keymap          13708  1 dell_wmi
iwlwifi               147953  1 iwldvm
cfg80211              409394  3 iwlwifi,mac80211,iwldvm
wmi                    18673  1 dell_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9472201 (9.4 MB)  TX bytes:565275 (565.2 KB)
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmx0      Link encap:Ethernet  HWaddr <MAC addr wmx0>  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

wmx0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: connecting

- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr wmx0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0  [DDW36503] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Kingsbury Arch:  Infra, <MAC addr Clarity_Connect_407>, Freq 2422 MHz, Rate 54 Mb/s, Strength 69 WPA2
    Ny state of mind ext1: Infra, <MAC addr 001244b56fb0>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    NY State of Mind:Infra, <MAC addr MKZ>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA
    Clarity_Connect_407: Infra, <MAC addr IthacaMed-PatientWiFi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    001244b56fb0:    Infra, <MAC addr DDW361150>, Freq 2452 MHz, Rate 54 Mb/s, Strength 87 WEP
    MKZ:             Infra, <MAC addr DDW36503>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    IthacaMed-PatientWiFi: Infra, <MAC address>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    NETGEAR Wi-fi:   Infra, <MAC address>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    DDW361150:       Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    DDW36503:        Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

wmx0      no frequency information.

lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #####

wmx0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Clarity_Connect_407>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Kingsbury Arch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004fa91577c97
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr 001244b56fb0>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Ny state of mind ext1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000001e8d63
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr MKZ>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NY State of Mind"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7b2295f14
                    Extra: Last beacon: 3256ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr DDW361150>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"001244b56fb0"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005879708586b
                    Extra: Last beacon: 56ms ago
          Cell 05 - Address: <MAC addr DDW36503>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"MKZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000268c28d2699
                    Extra: Last beacon: 3256ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"DDW361150"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000061a9add5c0
                    Extra: Last beacon: 6448ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003a115d34183
                    Extra: Last beacon: 6332ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"lightlink-swair"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004a6b70e
                    Extra: Last beacon: 6240ms ago
          Cell 09 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"DDW36503"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c80ccd188
                    Extra: Last beacon: 5988ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"DDW36503"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c81278e0b
                    Extra: Last beacon: 36ms ago

##### module infos #####

[iwldvm]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A7:FC:65:90:FC:4A:8D:85:9A:AE:BD:A2:CA:5D:D0:47:16:24:4F:A0
sig_hashalgo:   sha512

[iwlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005102bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000510Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A7:FC:65:90:FC:4A:8D:85:9A:AE:BD:A2:CA:5D:D0:47:16:24:4F:A0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

##### module parameters #####

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

##### /etc/modules #####

lp

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:0b:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   11.014976] iwlwifi 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.015104] iwlwifi 0000:05:00.0: irq 46 for MSI/MSI-X
[   11.639532] iwlwifi 0000:05:00.0: loaded firmware version 41.28.5.1 build 33926 op_mode iwldvm
[   11.786209] type=1400 audit(1407536617.201:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=490 comm="apparmor_parser"
[   11.786239] type=1400 audit(1407536617.201:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=484 comm="apparmor_parser"
[   11.786909] type=1400 audit(1407536617.201:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=490 comm="apparmor_parser"
[   11.786941] type=1400 audit(1407536617.201:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=484 comm="apparmor_parser"
[   12.585501] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   12.585506] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   12.585508] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   12.585511] iwlwifi 0000:05:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[   12.585615] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[   12.585825] iwlwifi 0000:05:00.0: RF_KILL bit toggled to disable radio.
[   12.643575] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.606731] i2400m_usb 2-1.5:1.0: firmware interface version 9.3.2
[   19.679180] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  244.884274] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[  252.206944] iwlwifi 0000:05:00.0: RF_KILL bit toggled to disable radio.
[  252.428501] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[  253.742233] iwlwifi 0000:05:00.0: RF_KILL bit toggled to disable radio.
[  257.108536] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[  259.006678] i2400m_usb 2-1.5:1.0: firmware interface version 9.3.2
[  260.220049] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[  260.220259] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[  260.444783] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[  260.444998] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[  260.550880] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  270.216793] wlan0: authenticate with <MAC address>
[  270.222358] wlan0: direct probe to <MAC address> (try 1/3)
[  270.426397] wlan0: direct probe to <MAC address> (try 2/3)
[  270.630422] wlan0: direct probe to <MAC address> (try 3/3)
[  270.834394] wlan0: authentication with <MAC address> timed out
[  279.036159] wlan0: authenticate with <MAC address>
[  279.040689] wlan0: send auth to <MAC address> (try 1/3)
[  279.147909] wlan0: send auth to <MAC address> (try 2/3)
[  279.251923] wlan0: send auth to <MAC address> (try 3/3)
[  279.355955] wlan0: authentication with <MAC address> timed out
[  555.271376] wlan0: authenticate with <MAC address>
[  555.284098] wlan0: direct probe to <MAC address> (try 1/3)

########## wireless info END ############

```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

