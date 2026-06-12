---
title: "AR8162 Wired internet disabled on Asus 1015e-ds03"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by Ms_Angel_D on 2014-01-12
Hello all,

I have an Asus 1015e-dso3 laptop. It came with ubuntu 12.04 installed, and everything was fine, except that the laptop came very strangly partitioned. There was about 150gb worth of space that wasn't being used and no partition manager would let me access so I could use it. Finally being a KDE fan at heart I decided to wipe it clean & just install Kubuntu 12.04 Everything is working fine except for some reason I only have wireless internet & can't get my wired internet working.

I have enabled backports and performed all updates and my laptop tells me there are no restricted drivers available.

I've tried to provide as much info as possible So here's the output of [Varun's Wireless script]("http://ubuntuforums.org/showpost.php?p=12350385"), it seems to do a pretty thorough job, even though it's my wired internet that's giving me trouble:

```

*************** info trace ***************

***** uname -a *****

Linux angel-laptop 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

***** lspci *****

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave Device [1a3b:1186]
	Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:115d]

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 001 Device 003: ID 13d3:5188 IMC Networks 
Bus 002 Device 003: ID 0a5c:21e8 Broadcom Corp. 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"Dallemagnes"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12756   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

ath9k                 132428  0 
mac80211              506862  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205774  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Dallemagnes] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Dragon's Lair:   Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 57 WPA2
    hipstumatic:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    teamarmbruster:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    *Dallemagnes:    Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 66 WPA
    Schnell45212:    Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA2
    linksys:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19
    Who-Dey Nation:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA
    Vineyard Central:Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA
    BUDWIRELESS:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WEP
    The Travis and Steve Show: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    NSA :            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA

  IPv4 Settings:
    Address:         192.168.1.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.4.4
    DNS:             8.8.8.8



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Dallemagnes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000448199180
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 000B44616C6C656D61676E6573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 331A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 341608080800000000000000000000000000000000000000
                    IE: Unknown: 3D1608080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Dragon's Lair"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009c0ee28486
                    Extra: Last beacon: 1324ms ago
                    IE: Unknown: 000D447261676F6E2773204C616972
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34020D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16020D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"hipstumatic"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002f0b817136e
                    Extra: Last beacon: 1312ms ago
                    IE: Unknown: 000B6869707374756D61746963
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3401001500000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010427974EECF6C52788C94000000000000102100046E6F6E65102300046E6F6E65102400046E6F6E651042001253657269616C204E756D62657220486572651054000800060050F204000110110016574E5232303030763428576972656C65737320415029100800022008103C0001011049000600372A000120
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BUDWIRELESS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c1781c9cf6
                    Extra: Last beacon: 844ms ago
                    IE: Unknown: 000B425544574952454C455353
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020015
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001efed869004
                    Extra: Last beacon: 680ms ago
                    IE: Unknown: 00200000000000000000000000000000000000000000000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Who-Dey Nation"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000300c46518a
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 000E57686F2D446579204E6174696F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B0001031047001006E9635B98C3CAA3DE995D4F8DABC645102100055A7958454C1023000A502D363630484E2D35311024000A502D363630484E2D353110420007393633363847571054000800060050F20400011011000A502D363630484E2D3531100800020084103C000101
                    IE: Unknown: DD090010180208F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"NSA "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a07bee2da
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 00044E534120
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a07bee804
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 00200000000000000000000000000000000000000000000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"teamarmbruster"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005b4c08a413
                    Extra: Last beacon: 532ms ago
                    IE: Unknown: 000E7465616D61726D62727573746572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180204F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Vineyard Central"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001efed87de7a
                    Extra: Last beacon: 592ms ago
                    IE: Unknown: 001056696E65796172642043656E7472616C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5396C6B49418C30B65FDBC1
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     87C8338518A200F45D72110
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5A4F26731216C44D9DA1D5C
depends:        ath
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8B429DBE4586F4065E2EA2E
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    9.346809] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[    9.381397] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.381416] ath9k 0000:02:00.0: setting latency timer to 64
[    9.390510] ath: EEPROM regdomain: 0x60
[    9.390512] ath: EEPROM indicates we should expect a direct regpair map
[    9.390517] ath: Country alpha2 being used: 00
[    9.390520] ath: Regpair used: 0x60
[    9.691946] Registered led device: ath9k-phy0
[   10.779682] Bluetooth: can't load firmware, may not work correctly
[   18.084248] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.087342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.263710] wlan0: authenticate with <MAC address removed> (try 1)
[   59.268088] wlan0: authenticated
[   59.292426] wlan0: associate with <MAC address removed> (try 1)
[   59.296829] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   59.296866] wlan0: associated
[   59.301857] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.802360] wlan0: no IPv6 routers present
[  703.363846] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  707.237598] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x103)
[  707.237612] ath9k 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xf7d80000)
[  707.237641] ath9k 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf7d00004)
[  707.237650] ath9k 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  707.237662] ath9k 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  710.808864] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  717.909253] wlan0: authenticate with <MAC address removed> (try 1)
[  717.911291] wlan0: authenticated
[  717.911708] wlan0: associate with <MAC address removed> (try 1)
[  717.915997] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[  717.916007] wlan0: associated
[  717.923915] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  728.539382] wlan0: no IPv6 routers present
[  728.847591] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  732.443591] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  735.605354] wlan0: authenticate with <MAC address removed> (try 1)
[  735.607337] wlan0: authenticated
[  735.607700] wlan0: associate with <MAC address removed> (try 1)
[  735.611996] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[  735.612004] wlan0: associated
[  735.617561] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  746.223948] wlan0: no IPv6 routers present

****************** done ******************


```
The output of sudo lshw -C network
```
*-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 6c:71:d9:7f:9b:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-58-generic firmware=N/A ip=192.168.1.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c3ffff ioport:e000(size=128)

```
The output of ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:542537 (542.5 KB)  TX bytes:542537 (542.5 KB)

wlan0     Link encap:Ethernet  HWaddr 6c:71:d9:7f:9b:9d  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6e71:d9ff:fe7f:9b9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14215278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4228474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20103309745 (20.1 GB)  TX bytes:495036621 (495.0 MB)
```

Thank you in advance,
Angel

---

### Post by chili555 on 2014-01-12
> Qualcomm Atheros AR8162 Fast Ethernet [[COLOR="#FF0000"]1969:1090[/COLOR]] (rev 10)Your ethernet device requires the driver alx which isn't present in 12.04 but is in 13.04 et seq. You could reinstall 13.10 or we could install the backported driver. Assuming the latter, please get a working wireless connection, open a terminal and do:

```
sudo apt-get install linux-headers-generic build-essential
```

Now download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10/backports-3.10-2.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10/backports-3.10-2.tar.bz2) Right-click it and select 'Extract Here.' Now back to the terminal:

```
cd ~/Desktop/backports-3.10-2
make defconfig-alx
make
sudo make install
sudo modprobe alx
```Note and post any errors. You may get a warning about signing that you may safely ignore.

Your ethernet should now be working.

---

### Post by Ms_Angel_D on 2014-01-12
> **chili555 said:**
> Your ethernet device requires the driver alx which isn't present in 12.04 but is in 13.04 et seq. You could reinstall 13.10 or we could install the backported driver. Assuming the latter, please get a working wireless connection, open a terminal and do:

```
sudo apt-get install linux-headers-generic build-essential
```

Now download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10/backports-3.10-2.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10/backports-3.10-2.tar.bz2) Right-click it and select 'Extract Here.' Now back to the terminal:

```
cd ~/Desktop/backports-3.10-2
make defconfig-alx
make
sudo make install
sudo modprobe alx
```Note and post any errors. You may get a warning about signing that you may safely ignore.

Your ethernet should now be working.

Thank you very much, I received no errors and now have a working ethernet :)

---

### Post by chili555 on 2014-01-12
Awesome! You will need to recompile whenever Update Manager installs a later kernel and asks you to reboot. Afterwards:```
cd ~/Desktop/backports-3.10-2
[COLOR="#FF0000"]make clean[/COLOR]
make defconfig-alx
make
sudo make install
sudo modprobe alx
```

I must apply for membership some day...

---

### Post by Ms_Angel_D on 2014-01-12
> **chili555 said:**
> Awesome! You will need to recompile whenever Update Manager installs a later kernel and asks you to reboot. Afterwards:```
cd ~/Desktop/backports-3.10-2
[COLOR="#FF0000"]make clean[/COLOR]
make defconfig-alx
make
sudo make install
sudo modprobe alx
```


Thank you I'll copy your instructions to evernote ;)

> **chili555 said:**
> I must apply for membership some day...

Go for it I would vote for you :)!!

---

