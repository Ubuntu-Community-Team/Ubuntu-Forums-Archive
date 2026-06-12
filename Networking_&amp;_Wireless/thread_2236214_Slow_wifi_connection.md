---
title: "Slow wifi connection"
date: 2014-07-25
forum: Networking &amp; Wireless
---

### Post by michaelq87 on 2014-07-25
Hi guys,

I'm working in a coworking space, and here everybody don't have any problem with the wifi, except me: sometimes i get disconnected and other times it goes really slow that i can't load even [www.google.com](www.google.com) .
Please help! :)

This is the output of the wireless report script:

```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux michael-N550JK 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


04:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave Device [1a3b:2126]
	Kernel driver in use: ath9k
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 003 Device 003: ID 13d3:5188 IMC Networks 
Bus 003 Device 002: ID 13d3:3402 IMC Networks 
Bus 003 Device 005: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626557  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
ath3k                  13318  0 
bluetooth             395423  12 bnep,ath3k,btusb,rfcomm


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"BETAHAUS_LEGACY"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=57.8 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:26  Invalid misc:1395   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 wlan0
10.1.0.0        0.0.0.0         255.255.0.0     U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search betahaus.bln


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [BETAHAUS_LEGACY] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           57 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    FRITZ!Box Fon WLAN 7170: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    WiFi Vive Back:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    BETAHAUS:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    innospace_legacy:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    Nikofilm M-appeal: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    this++:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    BETAHAUS_LEGACY: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *BETAHAUS_LEGACY:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Startnext_Guest: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Startnext Network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    ALICE-WLAN44:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    DIRECT-WJHowDo_Machine: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    epubli:          Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 69 WPA2
    epubli-lan:      Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 34 WPA2
    BETAHAUS:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    BETAHAUS:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    FEED WiFi:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    BETAHAUS:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    jovoto Trabi:    Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 77 WPA2


  IPv4 Settings:
    Address:         10.1.250.0
    Prefix:          16 (255.255.0.0)
    Gateway:         10.1.1.1


    DNS:             10.1.1.1


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


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"BETAHAUS_LEGACY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a8a83df4c
                    Extra: Last beacon: 264ms ago
                    IE: Unknown: 000F42455441484155535F4C4547414359
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 331AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000D00000000000000000000000000000000000000
                    IE: Unknown: 341606000D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Petobel-Wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000163287c9468
                    Extra: Last beacon: 3912ms ago
                    IE: Unknown: 000C5065746F62656C2D57696669
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 331AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000D00000000000000000000000000000000000000
                    IE: Unknown: 341601000D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"BETAHAUS_LEGACY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b6f743a89
                    Extra: Last beacon: 3576ms ago
                    IE: Unknown: 000F42455441484155535F4C4547414359
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 331AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001F00000000000000000000000000000000000000
                    IE: Unknown: 341601001F00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b6f6f9181
                    Extra: Last beacon: 3936ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001F00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1300156D00010100010207E581060027226A1347
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Nikofilm M-appeal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001632a85a160
                    Extra: Last beacon: 11296ms ago
                    IE: Unknown: 00114E696B6F66696C6D204D2D61707065616C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B28601001DAAA533F8103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020098127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050500000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000179d04e728f
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1300156D00010100010207E58106DC9FDB1A1C5B
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"WiFi Vive Back"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002af2409d2a
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 000E576946692056697665204261636B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 341606000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDB10050F204104A00011010440001021057000101103B00010310470010BA6DD3F4D6A958A596B8F96A685DB14B10210007756E6B6E6F776E10230018486F6D65506C756720415620576972656C6573732041502010240017486F6D65506C756720415620576972656C65737320415010420003312E301054000800060050F204000110110017486F6D65506C756720415620576972656C65737320415010080002200E103C0001011049000600372A000120
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"this++"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d6c9d9d5
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 0006746869732B2B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050C020300000000000000000000
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Startnext_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016329b44f2c
                    Extra: Last beacon: 9252ms ago
                    IE: Unknown: 000F53746172746E6578745F4775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a8b1f341a
                    Extra: Last beacon: 520ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1300156D00010100010207E581060027226A0C74
          Cell 11 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"innospace_legacy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00c80179d02aaa85
                    Extra: Last beacon: 208ms ago
                    IE: Unknown: 0010696E6E6F73706163655F6C6567616379
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 331AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000D00000000000000000000000000000000000000
                    IE: Unknown: 341606000D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Petobel-Wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001632849c180
                    Extra: Last beacon: 2788ms ago
                    IE: Unknown: 000C5065746F62656C2D57696669
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010142
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 13 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"jovoto Trabi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000e392e2a
                    Extra: Last beacon: 1716ms ago
                    IE: Unknown: 000C6A6F766F746F205472616269
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1607001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD840050F204104A0001101044000102103B0001031047001000000000000010000000C03F0E7BFB3C1021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110015574E44523337303028576972656C65737320415029100800020086103C000103
          Cell 14 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"epubli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000010fe5f5
                    Extra: Last beacon: 10028ms ago
                    IE: Unknown: 0006657075626C69
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706444520010B14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AED111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1609001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005f9cc9d3
                    Extra: Last beacon: 860ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037313730
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Startnext Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016329aaec3e
                    Extra: Last beacon: 9868ms ago
                    IE: Unknown: 001153746172746E657874204E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A000110104400010210470010F4F7EA607F0557FCB765B03051938370103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 17 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"FEED WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000118755ec18b
                    Extra: Last beacon: 8056ms ago
                    IE: Unknown: 0009464545442057694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 200100
                    IE: Unknown: 23021000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F207000101069072401D1D4D
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 18 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Petobel-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001632833e180
                    Extra: Last beacon: 4272ms ago
                    IE: Unknown: 000D5065746F62656C2D4775657374
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 19 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Petobel-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000163287d52ee
                    Extra: Last beacon: 3912ms ago
                    IE: Unknown: 000D5065746F62656C2D4775657374
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010008
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC0103FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 20 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Klebeland.de"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000fba8943180
                    Extra: Last beacon: 3608ms ago
                    IE: Unknown: 000C4B6C6562656C616E642E6465
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF111BFFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1602001500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000A00


##### iwlist channel #####


wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### modinfo #####


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     470F4A9FC9506B4AE23CF37
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0220d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512


##### modules #####


lp
rtc


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    1.354721] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f05)
[   13.242108] ath: phy0: Set parameters for CUS198
[   13.242110] ath: phy0: Set BT/WLAN RX diversity capability
[   13.248082] ath: phy0: Enable LNA combining
[   13.249316] ath: EEPROM regdomain: 0x60
[   13.249318] ath: EEPROM indicates we should expect a direct regpair map
[   13.249321] ath: Country alpha2 being used: 00
[   13.249322] ath: Regpair used: 0x60
[   16.370484] Bluetooth: Error in firmware loading err = -110,len = 448, size = 4096
[   16.370549] ath3k: probe of 3-5:1.0 failed with error -110
[   24.076380] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.079321] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  138.134445] wlan0: authenticate with <MAC address removed>
[  138.151591] wlan0: send auth to <MAC address removed> (try 1/3)
[  138.158901] wlan0: authenticated
[  138.160635] wlan0: associate with <MAC address removed> (try 1/3)
[  138.176119] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[  138.176164] wlan0: associated
[  138.176187] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  666.054696] wlan0: authenticate with <MAC address removed>
[  666.071940] wlan0: direct probe to <MAC address removed> (try 1/3)
[  666.274714] wlan0: direct probe to <MAC address removed> (try 2/3)
[  666.478910] wlan0: direct probe to <MAC address removed> (try 3/3)
[  666.683075] wlan0: authentication with <MAC address removed> timed out
[  666.924617] wlan0: authenticate with <MAC address removed>
[  666.941930] wlan0: direct probe to <MAC address removed> (try 1/3)
[  667.143492] wlan0: send auth to <MAC address removed> (try 2/3)
[  667.145907] wlan0: authenticated
[  667.147435] wlan0: associate with <MAC address removed> (try 1/3)
[  667.154553] wlan0: RX AssocResp from <MAC address removed> (capab=0x31 status=0 aid=16)
[  667.154616] wlan0: associated


########## wireless info END ############
```

---

### Post by varunendra on 2014-07-25
If you have admin access to the router/access-point, please try changing its encryption to pure WPA2-PSK with AES (CCMP). Currently it is set to WPA/WPA2 mixed mode with TKIP - avoid these.

Also try changing the channel to 1 or 11. Reboot the router after saving the changes.

Then in Ubuntu, if required, or if you can't change the encryption in the router try this -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Reboot and see if the connection is any better. If not, please post a fresh report of wireless_script (try the new one first - I remember it generated a blank file for you, but in case we are lucky this time..), plus the output of -
```
grep -iR [[:alnum:]] /sys/module/ath9k/parameters
```

**PS:**
Oh, and since you don't seem to be using IPv6, please set it to "Ignore" in Network Manager settings.

---

### Post by michaelq87 on 2014-07-28
Hi ,

I still have problems: 

1) I don't have admin access to the router, it's a public space. I could tell them to do it, it will be better also for all the other users (windows and mac os)?

2) I'd tried to run again the new script but it's not working, here is the error: sed: -e expression #1, char 368: unknown command: `*'
So I'd just run the old one:

```
 

########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux michael-N550JK 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


04:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2126]
    Kernel driver in use: ath9k
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 003 Device 004: ID 13d3:5188 IMC Networks 
Bus 003 Device 006: ID 13d3:3402 IMC Networks 
Bus 003 Device 002: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
ath3k                  13318  0 
mac80211              626557  1 ath9k
bluetooth             395423  12 bnep,ath3k,btusb,rfcomm
cfg80211              484040  3 ath,ath9k,mac80211


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"BETAHAUS_LEGACY"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:63   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 wlan0
10.1.0.0        0.0.0.0         255.255.0.0     U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search betahaus.bln


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [BETAHAUS_LEGACY] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    BETAHAUS:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    FRITZ!Box Fon WLAN 7170: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    jovoto Trabi:    Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 75 WPA2
    WiFi Vive Back:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    DIRECT-WJHowDo_Machine: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2
    FEED WiFi:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    ALICE-WLAN44:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    HP43B3A5:        Ad-Hoc, <MAC address removed>, Freq 2457 MHz, Rate 11 Mb/s, Strength 52
    epubli:          Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 70 WPA2
    Nikofilm M-appeal: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    kreuzwerker 2G:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Wifi vive Printer: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    good & plenty:   Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    this++:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    innospace_legacy:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    epubli-lan:      Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 64 WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    BETAHAUS:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    yield:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    ALICE-WLAN44:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Startnext Network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Startnext_Guest: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    BETAHAUS_LEGACY: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    BETAHAUS_LEGACY: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    BETAHAUS:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *BETAHAUS_LEGACY:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    BETAHAUS_LEGACY: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Petobel-Guest:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    BETAHAUS:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    BETAHAUS:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Petobel-Wifi:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BETAHAUS_LEGACY: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    FRITZ!Box Fon WLAN 7270: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2


  IPv4 Settings:
    Address:         10.1.250.0
    Prefix:          16 (255.255.0.0)
    Gateway:         10.1.1.1


    DNS:             10.1.1.1


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


##### iwlist #####


##### iwlist channel #####


wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### modinfo #####


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     470F4A9FC9506B4AE23CF37
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0220d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:CE:B2:C5:67:D2:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512


##### modules #####


lp
rtc


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    1.358115] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f05)
[   13.768384] ath: phy0: Set parameters for CUS198
[   13.768386] ath: phy0: Set BT/WLAN RX diversity capability
[   13.774348] ath: phy0: Enable LNA combining
[   13.775524] ath: EEPROM regdomain: 0x60
[   13.775526] ath: EEPROM indicates we should expect a direct regpair map
[   13.775528] ath: Country alpha2 being used: 00
[   13.775529] ath: Regpair used: 0x60
[   17.327605] Bluetooth: Error in firmware loading err = -110,len = 448, size = 4096
[   17.327669] ath3k: probe of 3-5:1.0 failed with error -110
[   24.167850] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.170911] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   64.354434] wlan0: authenticate with <MAC address removed>
[   64.377621] wlan0: send auth to <MAC address removed> (try 1/3)
[   64.393485] wlan0: authenticated
[   64.397477] wlan0: associate with <MAC address removed> (try 1/3)
[   64.403186] wlan0: RX AssocResp from <MAC address removed> (capab=0x31 status=0 aid=1)
[   64.403213] wlan0: associated
[   64.403222] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   64.453227] wlan0: authenticate with <MAC address removed>
[   64.470397] wlan0: send auth to <MAC address removed> (try 1/3)
[   64.473035] wlan0: authenticated
[   64.473475] wlan0: associate with <MAC address removed> (try 1/3)
[   64.481167] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=11)
[   64.481206] wlan0: associated
[   69.970715] wlan0: authenticate with <MAC address removed>
[   69.987841] wlan0: send auth to <MAC address removed> (try 1/3)
[   69.992451] wlan0: authenticated
[   69.993944] wlan0: associate with <MAC address removed> (try 1/3)
[   69.998228] wlan0: RX AssocResp from <MAC address removed> (capab=0x31 status=0 aid=1)
[   69.998253] wlan0: associated


########## wireless info END ############ 
```

And the command you told me: 

```
 /sys/module/ath9k/parameters/blink:0/sys/module/ath9k/parameters/bt_ant_diversity:0
/sys/module/ath9k/parameters/nohwcrypt:1
/sys/module/ath9k/parameters/btcoex_enable:0
/sys/module/ath9k/parameters/ps_enable:0



```

Thx for your help,
Mike

---

### Post by varunendra on 2014-07-29
> **michaelq87 said:**
> 1) I don't have admin access to the router, it's a public space. I could tell them to do it, **it will be better also for all the other users (windows and mac os)?**

We believe that it (WPA2-PSK with AES) is better for everyone, except those who may have really ancient devices that don't support WPA2 encryption (that generally means devices that are more than 10 yrs old).

Maybe you can convince the admins better by showing an official response regarding this from Intel : [https://communities.intel.com/message/214103#214103](https://communities.intel.com/message/214103#214103)

For the current state, I think there are only three more things left that can be further optimized. If they help, good. If not, the fourth option is to try compiling a newer driver (with no guarantee of better performance, just hope).

[indent]**1)** Try explicitly defining your country code for regdomain settings. Currently it has been defaulted to '00'. For example, if you are in USA, then the country code is 'US', and to explicitly define it -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Then reboot to let the change take effect. After reboot, run the following command to confirm the regdomain settings -
```
iw reg get
```
It should show "US", followed by its pertaining settings. Of course change the country code "US" (in caps) with your country's code. To find your country's RegDomain code, see this table : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

**2)** Make sure the "Power Management" isn't turned "On" when the performance goes down. To check it, use the command -
```
iwconfig
```
..and check the value of "Power Management" in the output. I suggest checking it often to make sure it is not automatically turning on. We recommend to keep it off all the time for optimal wifi performance. I'll suggest the ways to turn it off and keep it that way, if required.

**3)** Find the fastest DNS for your connection, and use that one(s) by defining them manually in Network Manager settings (Network Manager settings > edit your connection > IPv4 tab > set 'Method' to "Automatic (DHCP) address only" > put the IP address of the desired DNS in the "DNS servers" field > Save > Close).
To find the fastest DNS for you, you can use tools like "namebench" available in the repositories. To install it -
```
sudo apt-get install namebench
```
Then run it from either command line ("namebench" command), or, **Alt-F2 > type "namebench" > Enter**. Its GUI takes some time to open. When the GUI comes up, press "Start Benchmark" button and let it run and finish (may take a long time). When finished, it will show the test results and recommend the fastest DNS for you.

Apart from these, if your regdomain settings allow a Tx value higher than current value "15", plus IF the card has the capability to accept different values (not all cards support that), you may try forcing a higher Tx value like "20" with command -
```
sudo iwconfig wlan0 txpower 20
```
..but first, not all cards support that, and second, it is just an available option I know of - though so far I have never seen it helping someone's connectivity issue (but then people rarely try it).[/indent]

If none of these can help, our last hope would be either a newer driver, or someone who knows a better solution than these.

---

### Post by michaelq87 on 2014-08-04
Nothing to do.. I still have problems :(

I tried also to incrase tx value, but I think my card doesn't support that 'cause i can't change it

---

### Post by varunendra on 2014-08-04
Maybe show us a fresh report of the script. I may not be able to respond now, partly because I don't have much time for next few days, and partly because I may not have anymore ideas. But with a new report, I may try to seek help from others if needed, and if they can be available.

Apart from the script report, please also post the output of -
```
grep -R [[:alnum:]] /sys/module/ath9k/parameters
```

And the practical speed (result of speedtest.net) you are currently getting.

---

