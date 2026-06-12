---
title: "HP Envy 15TS RTL8188EE 14.04LTS"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by SLaCK3r on 2014-04-19
Sorry, I know you probably get sick of the same posts, but I'm stumped.

I installed 14.04LTS yesterday, and it's amazing. I seriously only have one big issue with it, my wifi will connect and get full signal, but it cuts out during speed tests and seems very slow.

I ran many speed tests and it starts at like 16Mbps which is normal for my house, but then it will cut out and stop sending to the speedtest server and I notice it when I do anything on the internet. It's horribly slow. 

I've tried many things that Chili has posted before. I installed and compiled "Backports-3.12-1" and that fixed it sort-of. Originally I was getting 2Mbps. Now I'm getting 16, until it (often) cuts out. That's when I came here. 

```

########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux danny-HP-ENVY-TS-15-Notebook-PC 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee

0f:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:1963]
	Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 064e:9301 Suyin Corp. 
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 005: ID 138a:0050 Validity Sensors, Inc. 
Bus 003 Device 004: ID 0eef:a103 D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

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

wlan0     IEEE 802.11bgn  ESSID:"belkin3131"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:192   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search FBI Surveillance Van

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

- Device: wlan0  [belkin3131] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
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
    Netgear 3131:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    The Angry Chamber: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Monr Cnty Drg Suppress. #2: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *belkin3131:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    Buckley Network: Infra, <MAC address removed>, Freq 2412 MHz, Rate 48 Mb/s, Strength 100 WEP
    frankenburger2:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    casenet:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    steelers:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    SLYNET:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.2.31
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"belkin3131"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000058a748135c
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A62656C6B696E33313331
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD990050F204104A00011010440001021041000100103B00010310470010AD99B3C9129AFB40EC9BB2BC1BF81AC31021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303220763110240007312E30302E30361042000E31323131323247463130313033361054000800060050F204000110110014506C617920576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"SLYNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004dc37c04183
                    Extra: Last beacon: 8312ms ago
                    IE: Unknown: 0006534C594E4554
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 05050002000040
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFF191BFFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD360050F204104A00011010440001021057000101104700106FF19BBFBAD50378EB374CA7EB0F1BC8103C0001031049000600372A000120
                    IE: Unknown: DD09001018020CF03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Buckley Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    ESSID:"\x01\x00\x00\x0F\xAC\x04\x01\x00\x00\x0F\xAC\x04\x01\x00\x00\x0F\xAC\x02\x00\x00"
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 22.5 Mb/s
                    Mode:Master
                    Extra:tsf=00000152a4959180
                    Extra: Last beacon: 8304ms ago
                    IE: Unknown: 000F4275636B6C6579204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400030100
                    IE: Unknown: 2A0100
                    IE: Unknown: 00140100000FAC040100000FAC040100000FAC020000
                    IE: Unknown: 32043048602D
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 341601080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A2C2C01C800140000001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101090903A4000027A4000042435E0062322F2F
                    IE: Unknown: DD0900007F01010100FF7F
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-14 dBm  
                    Encryption key:on
                    ESSID:"Netgear 3131"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000439497ccf4c
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000C4E6574676561722033313331
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 341601080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Monr Cnty Drg Suppress. #2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000439497c11d1
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001A4D6F6E7220436E7479204472672053757070726573732E202332
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201018E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDA70050F204104A0001101044000102103B000103104700100000000000001000000000095B0765721021000741746865726F731023000D4D6F64656C4E616D65486572651024000F4D6F64656C4E756D626572486572651042001053657269616C4E756D626572486572651054000800060050F20400011011000A4578616D706C655765701008000201FF103C000103104900140024E26002000101600000020001600100020001
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000034c722180
                    Extra: Last beacon: 7288ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080C00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010107000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080C00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0C00156D0001000400E5020014
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"The Angry Chamber"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000034c880180
                    Extra: Last beacon: 5876ms ago
                    IE: Unknown: 001154686520416E677279204368616D626572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001D00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F202010109000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001D00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0C00156D0001000000E5020014
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c233dcf180
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301690320
                    IE: Unknown: DD0E0017F20700010106001CB3ACEBB0
                    IE: Unknown: DD0B0017F2010001010000000B
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"steelers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006a550cf7180
                    Extra: Last beacon: 6600ms ago
                    IE: Unknown: 0008737465656C657273
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6F1003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D16060D0600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336F1003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C34060D0600000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001011049000600372A000120
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Frontier 1309"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000021ca36b180
                    Extra: Last beacon: 6576ms ago
                    IE: Unknown: 000D46726F6E746965722031333039
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 341606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### lsmod #####

rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     1B8E36556B30AA35325F55D
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
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

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   12.112657] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   12.112730] rtl8188ee 0000:07:00.0: irq 46 for MSI/MSI-X
[   12.128279] Modules linked in: snd_seq rtl8188ee snd_seq_device rtl_pci snd_timer rtlwifi mac80211 snd cfg80211 lpc_ich(+) i915(+) rtsx_pci_ms memstick soundcore mei_me mei ttm drm_kms_helper drm i2c_algo_bit wmi(+) video hp_accel(+) lis3lv02d input_polldev intel_smartconnect(+) mac_hid parport_pc ppdev lp parport hid_generic usbhid hid rtsx_pci_sdmmc r8169 ahci rtsx_pci libahci mii
[   12.214871] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.215005] rtlwifi: wireless switch is on
[   14.661919] hda-intel 0000:00:03.0: Applying patch firmware 'hda-jack-retask.fw'
[   14.662053] hda-intel 0000:00:1b.0: Applying patch firmware 'hda-jack-retask.fw'
[   16.280656] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.268035] wlan0: authenticate with <MAC address removed>
[   17.268124] wlan0: send auth to <MAC address removed> (try 1/3)
[   17.269541] wlan0: authenticated
[   17.269660] rtl8188ee 0000:07:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   17.271503] wlan0: associate with <MAC address removed> (try 1/3)
[   17.274029] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   17.274154] wlan0: associated
[   17.274161] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  101.881199] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  103.275874] wlan0: authenticate with <MAC address removed>
[  103.295720] wlan0: send auth to <MAC address removed> (try 1/3)
[  103.297600] wlan0: authenticated
[  103.299466] wlan0: associate with <MAC address removed> (try 1/3)
[  103.302626] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[  103.302741] wlan0: associated
[  103.302762] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  260.977384] waiting module removal not supported: please upgrade<6>[ 1117.537582] wlan0: Connection to AP <MAC address removed> lost
[ 1120.884359] wlan0: authenticate with <MAC address removed>
[ 1120.901516] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1120.919549] wlan0: authenticated
[ 1120.921168] wlan0: associate with <MAC address removed> (try 1/3)
[ 1120.936675] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 1120.936808] wlan0: associated
[ 1120.936829] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1551.385149] wlan0: Connection to AP <MAC address removed> lost
[ 1554.999095] wlan0: authenticate with <MAC address removed>
[ 1555.018375] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1555.122183] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1555.128018] wlan0: authenticated
[ 1555.130179] wlan0: associate with <MAC address removed> (try 1/3)
[ 1555.133410] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 1555.133559] wlan0: associated
[ 1706.635731] wlan0: Connection to AP <MAC address removed> lost
[ 1709.810131] wlan0: authenticate with <MAC address removed>
[ 1709.828448] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1709.829923] wlan0: authenticated
[ 1709.832078] wlan0: associate with <MAC address removed> (try 1/3)
[ 1709.835370] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 1709.835505] wlan0: associated

########## wireless info END ############
```

---

### Post by praseodym on 2014-04-19
Try to change the encryption mode to pure WPA2-AES (CCMP) instead of mixed mode WPA/WPA2. Check the router manual

---

### Post by SLaCK3r on 2014-04-19
Hi. This seems to be working. I switched WiFi networks and this one appears to be more reliable. I'll have to wait until tomorrow when I go back to my University to see if those networks provide a reliable connection.

---

### Post by praseodym on 2014-04-19
Check now the difference to Cell 01 from above for WPA2 only. Scan you networks in your univ. accordingly.

---

### Post by SLaCK3r on 2014-04-19
```
      Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Monr Cnty Drg Suppress. #2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000439497c11d1
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001A4D6F6E7220436E7479204472672053757070726573732E202332
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201018E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDA70050F204104A0001101044000102103B000103104700100000000000001000000000095B0765721021000741746865726F731023000D4D6F64656C4E616D65486572651024000F4D6F64656C4E756D626572486572651042001053657269616C4E756D626572486572651054000800060050F20400011011000A4578616D706C655765701008000201FF103C000103104900140024E26002000101600000020001600100020001
```

And this is the Network I used previously: 

```
 Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"belkin3131"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000058a748135c
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A62656C6B696E33313331
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD990050F204104A00011010440001021041000100103B00010310470010AD99B3C9129AFB40EC9BB2BC1BF81AC31021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303220763110240007312E30302E30361042000E31323131323247463130313033361054000800060050F204000110110014506C617920576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

What exactly is causing the difference? They're both WPA2...all I can see is that Cell 01 is CCMP and Cell 05 is TKIP

---

### Post by praseodym on 2014-04-20
```
                    IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2[/COLOR] Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: [COLOR="#FF0000"]WPA[/COLOR] Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```
They are both mixed WPA/WPA2.

---

### Post by SLaCK3r on 2014-04-20
Well I still have the problem at my University. I will have a connection, then the WiFi will become slow/drop, then it will pick back up again...I am thinking there might not be anything I'm able to do about it. 

It's irritating! I like this operating system a lot. I was hoping I would be able to replace Windows 8.1 with it. Does anyone have any ideas?

---

### Post by praseodym on 2014-04-21
Lets try Wicd instead:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Check via "sudo iwlist scan" the encryption modes as described above in your university. Wicd brings a lot of templates, e.g. for mixed mode. Choose wlan0 as interface name and wext as driver in Wicd.

---

### Post by SLaCK3r on 2014-04-21
> **praseodym said:**
> Lets try Wicd instead:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Check via "sudo iwlist scan" the encryption modes as described above in your university. Wicd brings a lot of templates, e.g. for mixed mode. Choose wlan0 as interface name and wext as driver in Wicd.

I tried that, and it did not help :/

Good news. For anyone reading this, I own a 2013 HP Envy 15 TouchSmart. I have found a fix (well sort of)! Ubuntu 14.04LTS seems to be just too new and not ready to support this PC's wireless card. However, Ubuntu 12.04LTS works fantastically on this PC. If anyone becomes as frustrated as me, just downgrade :)

---

### Post by SLaCK3r on 2014-04-24
NEW UPDATE: After reading [http://askubuntu.com/questions/451724/wireless-connection-slow-inconsistent-after-fresh-install-ubuntu-14-04-realtek](http://askubuntu.com/questions/451724/wireless-connection-slow-inconsistent-after-fresh-install-ubuntu-14-04-realtek) and [http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

I have gotten the rtl8188ee to work well (so far) in 14.04. I downgraded the kernel to 13.14.1 and it works great!

---

### Post by samfraser on 2014-04-25
Hey thanks! I've had the same problem for some time with exactly the same RTL chip and Laptop and this solved the problem, thanks for sharing!  

Ubuntu...this is shoddy work!! No wonder Microsoft rules the world!

---

### Post by samfraser on 2014-05-03
Update, unfortunately there is still a problem with the wireless randomly hanging with all packets dropping, the connection recovers eventually but that fastest way to recover is to disconnect and reconnect, any idea's anyone?

---

### Post by thejacobisreal on 2014-05-03
Changing the Auth to WPA2-AES and the channel to 2, as well as upgrading the kernel to 3.14.1 resolved the issue.  I also removed B - so I am only using G/N to connect rather than B/G/N.

Note: Using AES rather than mixed or TKIP is more secure anyway and I would recommend it.

---

### Post by samfraser on 2014-05-09
I actually found getting the latest driver fixed the problem in the end, i've been good for a few weeks now.  it's still a good idea to upgrade the kernel cause my touchpad wasn't working great with the "shipped" 14.4 kernel.
copy past this to get the lastest drivers

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
echo "options rtl8188ee ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8188ee.conf
```

---

