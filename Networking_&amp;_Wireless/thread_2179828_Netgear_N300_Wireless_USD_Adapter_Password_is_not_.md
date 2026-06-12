---
title: "Netgear N300 Wireless USD Adapter: Password is not recongized"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by nzy102 on 2013-10-10
Hi Everyone,

Please forgive me to repeat the subject which has been posted many times by others. I did go through all the related posts and now I am able to see all available wifi networks. However, when I chose my network and typed the right password, ubuntu kept asking for password every 30 secs or so. I am pretty much that I typed in right password. 

I ran wireless_script posted on the forum and the output is posted below. Thank you in advance for help! 

P.S: I have ubuntu 13.04 (64 bits) on my laptop and installed bcmn43xx64.inf as wireless driver. 


*************** info trace ***************

***** uname -a *****

Linux lionHeart 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11g  ESSIDff/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Managementff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****


***** lsmod *****

rt2800pci              18582  0 
rt2800lib              66507  1 rt2800pci
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54925  3 rt2x00pci,rt2800lib,rt2800pci
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              511019  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
ndiswrapper           283323  0 

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [NingsNetwork] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connecting (need authentication)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Sweethouse:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA
    U+zone:          Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    U+NetD4FB:       Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 60 WPA2
    ATT840:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    WARJEV0327:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    Bard:            Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 59 WPA2
    2WIRE848:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA
    t&j-NG:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    belkin.c05:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ATT408:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    ATT640:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    SARNE:           Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 55 WPA2
    A-Rene:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    NGUERRERO:       Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Cisco26096:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    FBI:             Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WPA2
    NewSombrero:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    MGL:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    ernesto:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    jieun:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WEP
    Ochoojos:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 37 WPA2
    kc9423005:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA2
    NingsNetwork:    Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    sombrero:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.162
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



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
                    ESSID:"NingsNetwork"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000C4E696E67734E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402051900000000000000000000000000000000000000
                    IE: Unknown: 3D1602051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8B0050F204104A0001101044000102103B00010310470010000000000000100000000026F2F629C31021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001B574E5231303030763228576972656C6573732041502D322E344729100800020086103C000103
          Cell 02 - Address: <MAC address removed>
                    ESSID:"U+NetD4FB"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0009552B4E657444344642
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34030D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16030D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 03 - Address: <MAC address removed>
                    ESSID:"U+zone"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006552B7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34030D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16030D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 04 - Address: <MAC address removed>
                    ESSID:"kc9423005"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00096B6339343233303035
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880001DD1AF0670103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601030100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000073127A
                    IE: Unknown: DD07000C4303000000
          Cell 05 - Address: <MAC address removed>
                    ESSID:"belkin.c05"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000A62656C6B696E2E633035
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD990050F204104A00011010440001021041000100103B00010310470010396C9B98C77A3214FC97224848ECFA0E1021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303220763110240007312E30302E30361042000E31323131323247463130343731321054000800060050F204000110110014506C617920576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180206F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    ESSID:"ATT840"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006415454383430
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001F00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    ESSID:"SARNE"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00055341524E45
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605030400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050014127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A8805C571AC01D7010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 08 - Address: <MAC address removed>
                    ESSID:"ATT000"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006415454303030
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    ESSID:"t&j-NG"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000674266A2D4E47
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B00010310470010DCCBDE7808F6AAF23C0C5CE7247EA00B1021000D4E4554474541522C20496E632E10230008574E44523333303010240008574E4452333330301042000230311054000800060050F204000110110008574E445233333030100800020084103C000103
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    ESSID:"Bard"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000442617264
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD890050F204104A0001101044000102103B00010310470010E247280134828BAC5063CC324C2295D11021000D4E4554474541522C20496E632E1023000A574E44523334303076331024000A574E44523334303076331042000230311054000800060050F20400011011000A574E4452333430307633100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    ESSID:"Sweethouse"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000A5377656574686F757365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180206F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    ESSID:"FBI"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0003464249
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD890050F204104A0001101044000102103B00010310470010B659FD07186C6F3822678A87F6DC261A1021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180207F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    ESSID:"2WIRE848"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00083257495245383438
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303232313031393035353834381021000B32576972652C20496E632E10230011323730314847562D42204761746577617910240011323730314847562D4220476174657761791042000C3232313031393035353834381054000800060050F20400011011000A686F6D65706F7274616C10080002008E
          Cell 14 - Address: <MAC address removed>
                    ESSID:"WARJEV0327"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000A5741524A455630333237
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD770050F204104A0001101044000102103B0001031047001039FB8604B0C9B55E5964AF359C64D3C3102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180204F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: <MAC address removed>
                    ESSID:"ATT392"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006415454333932
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: <MAC address removed>
                    ESSID:"A-Rene"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006412D52656E65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050200A0127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555300010B10
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B000103104700108EA0C09AF2D5851C5D31CCB25596DEA510210006442D4C696E6B102300074449522D3831351024000830303030303030301042000830303030303030301054000800060050F2040001101100074449522D383135100800020082103C000103
          Cell 17 - Address: <MAC address removed>
                    ESSID:"ATT408"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006415454343038
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 18 - Address: <MAC address removed>
                    ESSID:"ATT640"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006415454363430
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.1.1

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
blacklist rtl8192cu

***** modinfo *****

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     A40A95D1558A66562B223A2
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     B68330971444C000132AEFA
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     4C55FBC01E873875F9583CA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     101F39DDF5F96BC8EA5BF21
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-31-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.58
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     B8626D54838746E24FF0F6A
depends:        
vermagic:       3.8.0-31-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0846:0x9020 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   18.823432] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   19.622540] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   19.881048] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[   19.883039] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   21.504492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.504709] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.250481] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1288.601113] ndiswrapper: device wlan0 removed
[ 1288.611141] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 1288.872175] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 1289.134638] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[ 1289.137096] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 1289.161156] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1289.161383] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1315.266595] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1341.441221] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 1470.840721] ndiswrapper: device wlan0 removed
[ 1470.864491] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 1471.124441] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 1471.124449] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmn43xx32'
[ 1471.124547] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmn43xx32'
[ 1503.834006] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 1504.088233] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 1504.346612] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[ 1504.349146] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 1504.371117] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1504.371384] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1538.700417] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2433.099938] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)

****************** done ******************

---

### Post by chili555 on 2013-10-10
DISCLAIMER: Your device is very tricky to get going. Nothing is guaranteed.

Why is rt2800pci loaded? It is not relevant to your USB. Do you have an internal wireless device that isn't working as expected? I'd sooner troubleshoot it and show your Netgear my sledgehammer.

What do you make of this?> [ 1471.124441] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BYikes.

I'm gonna hate myself for even trying this.

---

### Post by nzy102 on 2013-10-10
Hi Chili555,

thank you for your reply. I do have an internal wireless card but it stopped working for both windows and ubuntu a while ago. That was why I bought a usb adapter. I did install a 64bit driver bcmn43xx64.inf on my laptop. Can you let me know what I should try? I am a newbie with linux. Many thanks.

---

### Post by varunendra on 2013-10-10
Hi nzy102,

As you can see yourself, the unformatted output in your original post is looking awfully long and ugly. You should edit it to wrap the output part within 'Code' tags.

Just click on "Edit" button, and type **[noparse]```
[/noparse]** at the beginning, and **[noparse]
```[/noparse]** at the end of the output part. You can follow the "Using Code Tags" link in my signature to see an example with screenshots.

---

### Post by chili555 on 2013-10-10
First, let's blacklist the internal. Please open a terminal and do:```
sudo -i
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Next, it appears that you have both the 32- and 64-bit files on your system and ndiswrapper is trying to load both:> [ 1471.124449] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmn43xx[COLOR="#FF0000"]32[/COLOR]'
[ 1471.124547] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmn43xx32'
[ 1503.834006] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 1504.088233] ndiswrapper: driver bcmn43xx[COLOR="#FF0000"]64[/COLOR] (,08/26/2009, 5.10.79.30) loadedLet's check and remove, if necessary, the 32-bit files:```
ls /etc/ndiswrapper
```You probably have both bcmn43xx64 and bcmn43xx32. If so, remove the 32s:```
sudo rm -rf /etc/ndiswrapper/bcmn43xx32
```Please proofread carefully before you press Enter. 'rm' is permanent and potentially disastrous if used improperly. If in doubt, *STOP* and ask. 

Reboot and let us have your report.

---

