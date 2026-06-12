---
title: "HP Laptop (intel) internet problems, Ubuntu 14.04 LTS"
date: 2014-05-30
forum: Networking &amp; Wireless
---

### Post by gijs2 on 2014-05-30
Hi,

I have 2 problems with my network.

 1. When I disconnect from my wireless network I can't seem to reconnect with ANY network.
 2. My internet gets from time to time really slow and i wont be able to load a internet page (it is not my internet since my other pc has no problems with it).

Below is the wireless script, hopefully there is something there to fix my problems!

```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux Gijs 3.14.4-031404-generic #201405130853 SMP Tue May 13 12:54:33 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Hewlett-Packard Company Device [103c:2163]
    Kernel driver in use: r8169


##### lsusb #####


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 05c8:0361 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 046d:c069 Logitech, Inc. M500 Laser Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


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


wlan0     IEEE 802.11bgn  ESSID:"TP-LINK_99F562"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC address removed>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1


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


- Device: wlan0  [TP-LINK_99F562 1] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    VGV75191674C5:   Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    UPC WifiSpots:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UPC243087066:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Thomson0F024A:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    Thomson0EF3F2:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    UPC0042658:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    kvyb798th763cgh4589ft7u89b7j654h: Infra, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 100 WPA
    City_Bar:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA
    UPC012553:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    UPC WifiSpots:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2 Enterprise
    *TP-LINK_99F562: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 80 WPA2
    VGV7519B99CE5:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    UPC1922345:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    123WiFi:         Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Duinzoom_Boven_2G: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Duinzoom:        Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 64 WPA
    UPC WifiSpots:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    Marjolein:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2


  IPv4 Settings:
    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


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
managed=true


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_99F562"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b4b68f219d
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000E54502D4C494E4B5F393946353632
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1608071500000000000000000000000000000000000000
                    IE: Unknown: 341608071500000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=24 dBm  
                    Encryption key:on
                    ESSID:"UPC012553"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014816d84e0
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0009555043303132353533
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"UPC WifiSpots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014816d8e67
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D555043205769666953706F7473
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=20 dBm  
                    Encryption key:on
                    ESSID:"UPC WifiSpots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000025ecc2fbbb
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D555043205769666953706F7473
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"UPC0042658"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000025ecc3047b
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000A55504330303432363538
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180206F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"VGV7519B99CE5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005ff1d91b14e
                    Extra: Last beacon: 4148ms ago
                    IE: Unknown: 000D56475637353139423939434535
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030037127A
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=24 dBm  
                    Encryption key:on
                    ESSID:"Thomson0EF3F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d4f0163f50
                    Extra: Last beacon: 4020ms ago
                    IE: Unknown: 000D54686F6D736F6E304546334632
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010C6841213A5D259088E40E716289A8757103C000101
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081100000000000000000000000000000000000000
          Cell 08 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Duinzoom_Boven_2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d2e1150def6
                    Extra: Last beacon: 192ms ago
                    IE: Unknown: 00114475696E7A6F6F6D5F426F76656E5F3247
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607081100000000000000000000000000000000000000
                    IE: Unknown: DD270050F204104A00011010440001021047001097314A42477090E897AC851A682B4B39103C000103
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"VGV75191674C5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000638e9c8f15f
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 000D56475637353139313637344335
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 05050001000005
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1608000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040017127A
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Thomson0F024A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000136264f33ed
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 000D54686F6D736F6E304630323441
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD09001018020000050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"City_Bar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b3b19180
                    Extra: Last beacon: 3800ms ago
                    IE: Unknown: 0008436974795F426172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD1E00904C334E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1604051B00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"UPC243087066"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000248fab15d
                    Extra: Last beacon: 3492ms ago
                    IE: Unknown: 000C555043323433303837303636
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B286015CA39DC1A728103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0103FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000015127A
                    IE: Unknown: DD07000C4307000000
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s
                    Mode:Master
                    Extra:tsf=000017c86a2f9296
                    Extra: Last beacon: 372ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01028284
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000


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
          Current Frequency:2.447 GHz (Channel 8)


##### lsmod #####


rtl8188ee              96035  0 
rtl_pci                27261  1 rtl8188ee
rtlwifi                64281  2 rtl_pci,rtl8188ee
mac80211              676910  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              531467  2 mac80211,rtlwifi


##### modinfo #####


filename:       /lib/modules/3.14.4-031404-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     4D0248920A8ABAB530716AA
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.14.4-031404-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D5:63:86:FC:56:81:3D:44:5B:AC:C2:60:F4:1C
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


filename:       /lib/modules/3.14.4-031404-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B07D1002FC86501951333AE
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.14.4-031404-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D5:63:86:FC:56:81:3D:44:5B:AC:C2:60:F4:1C
sig_hashalgo:   sha512


filename:       /lib/modules/3.14.4-031404-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BACE38460F5E5294FE27C59
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.14.4-031404-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D5:63:86:FC:56:81:3D:44:5B:AC:C2:60:F4:1C
sig_hashalgo:   sha512


##### modules #####


lp
rtc
rtl8188ee


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
blacklist ath9k


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


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   10.830768] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   11.186199] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.186401] rtlwifi: wireless switch is on
[   28.470579] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.880163] wlan0: authenticate with <MAC address removed>
[   29.890253] wlan0: send auth to <MAC address removed> (try 1/3)
[   29.893490] wlan0: authenticated
[   29.895293] wlan0: associate with <MAC address removed> (try 1/3)
[   29.899042] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   29.899156] wlan0: associated
[   29.899167] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3033.247353] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3036.504849] rtlwifi: wireless switch is on
[ 3039.220827] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3040.950522] wlan0: authenticate with <MAC address removed>
[ 3040.970061] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3040.973080] wlan0: authenticated
[ 3040.973751] wlan0: associate with <MAC address removed> (try 1/3)
[ 3040.977508] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 3040.977616] wlan0: associated
[ 3040.977625] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3040.988351] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 3041.020084] wlan0: authenticate with <MAC address removed>
[ 3041.030179] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3041.032249] wlan0: authenticated
[ 3041.033725] wlan0: associate with <MAC address removed> (try 1/3)
[ 3041.037489] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 3041.037593] wlan0: associated


########## wireless info END ############
```

---

### Post by Harsh_Parikh on 2014-05-30
Did you try to go any website through its ip-address..??

---

### Post by gijs2 on 2014-05-30
> **Harsh_Parikh said:**
> Did you try to go any website through its ip-address..??

Erm... how? :p

---

### Post by Harsh_Parikh on 2014-05-30
Type in terminal : ping [www.]("http://www.")_*yourwebsitename*_.com....replace underlined with any website's name....Note ip-address looks like 123.456.789.012 
a number divided into 4 parts and separated with "." it can be 2 or 3 digits in any of the 4 parts....

---

### Post by gijs2 on 2014-05-30
> **Harsh_Parikh said:**
> Type in terminal : ping [www.]("http://www.")_*yourwebsitename*_.com....replace underlined with any website's name....Note ip-address looks like 123.456.789.012 
a number divided into 4 parts and separated with "." it can be 2 or 3 digits in any of the 4 parts....

It works, no errors there

```
ping www.google.com
PING www.google.com (74.125.136.105) 56(84) bytes of data.
64 bytes from ea-in-f105.1e100.net (74.125.136.105): icmp_seq=1 ttl=48 time=101 ms
64 bytes from ea-in-f105.1e100.net (74.125.136.105): icmp_seq=2 ttl=48 time=12.1 ms
64 bytes from ea-in-f105.1e100.net (74.125.136.105): icmp_seq=3 ttl=48 time=407 ms
64 bytes from ea-in-f105.1e100.net (74.125.136.105): icmp_seq=4 ttl=48 time=148 ms
^X64 bytes from ea-in-f105.1e100.net (74.125.136.105): icmp_seq=5 ttl=48 time=116 ms

```

---

### Post by Harsh_Parikh on 2014-05-30
Sorry,I forgot to mention that you would have to do this to your HP Laptop,which has network problem...and what you got as an ip-address of google site,copy and paste that number(ip)to your browser's address bar....I think it would load the homepage of google immediately.....

---

### Post by gijs2 on 2014-05-30
> **Harsh_Parikh said:**
> Sorry,I forgot to mention that you would have to do this to your HP Laptop,which has network problem...and what you got as an ip-address of google site,copy and paste that number(ip)to your browser's address bar....I think it would load the homepage of google immediately.....

It does, but i don't want to get the ip for every single website...

---

### Post by Harsh_Parikh on 2014-05-30
Tell me...which one consumes less time to load the page...???through ip or through address...??Because I think there has to be a way from which we can redirect to sites through its ip....neither finding ip's for every websites nor with the command ping.....

---

### Post by gijs2 on 2014-05-31
> **Harsh_Parikh said:**
> Tell me...which one consumes less time to load the page...???through ip or through address...??Because I think there has to be a way from which we can redirect to sites through its ip....neither finding ip's for every websites nor with the command ping.....

I think it's faster through IP.

---

### Post by Harsh_Parikh on 2014-05-31
OK....so,i have found something about which i think that it would be useful to you,if you interested....Go to 66.28.139.176 and register you account....and then find any website's ip address and go to that ip.....

---

### Post by gijs2 on 2014-05-31
> **Harsh_Parikh said:**
> OK....so,i have found something about which i think that it would be useful to you,if you interested....Go to 66.28.139.176 and register you account....and then find any website's ip address and go to that ip.....

The website doesn't work for me.

---

### Post by praseodym on 2014-05-31
Try to update the driver:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot. The "ee" driver is also inside that package.

---

### Post by gijs2 on 2014-05-31
> **praseodym said:**
> Try to update the driver:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot. The "ee" driver is also inside that package.

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
```

That gave me an error something like "Undefined variable"

---

### Post by praseodym on 2014-05-31
Did you copy/paste the line? $ is the Dollar

---

### Post by gijs2 on 2014-05-31
> **praseodym said:**
> Did you copy/paste the line? $ is the Dollar

Yeah I did

---

### Post by gijs2 on 2014-06-01
Bump~

---

