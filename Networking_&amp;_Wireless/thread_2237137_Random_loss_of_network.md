---
title: "Random loss of network"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by Nolster10 on 2014-07-30
Yes, its another one of these. I know this is always asked but, I've gone through multiple solutions with no luck. So hello everyone! My computer seems to disconnect from my network, and says its out of range, although other networks are still visible. I'm not 12 feet away from the router with only a wall separating me and the router, other laptops have no issues, and restarting the router and modem has done nothing. The only temporary solution is to disable my wifi and enable it again. Thank you in advance :) .

```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux nolan-Satellite-L675D 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]
    Kernel driver in use: rtl8192ce
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fd00]
    Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 002: ID 04f2:b1d6 Chicony Electronics Co., Ltd CNF9055 Toshiba Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi


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


wlan0     IEEE 802.11bgn  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:179   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


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


- Device: wlan0  [NETGEAR] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    belkin.648:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    xfinitywifi:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    belkin.e12.guests: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    *NETGEAR:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    HOME-0E94-2.4:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    NETGEAR-2.4-G_EXT: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    Sith Academy:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HOME-35F8_EXT:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    HOME-5D22:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ddcfa681d
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a38314abb5
                    Extra: Last beacon: 4180ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504008A127A
                    IE: Unknown: DD07000C4303000000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Barron Home 2.4ghz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a3738c13a0
                    Extra: Last beacon: 140ms ago
                    IE: Unknown: 0012426172726F6E20486F6D6520322E3467687A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401020008
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A000110104400010210470010B0C98B8012607EA641A71C10CE5C2495103C0001031049000600372A000120
                    IE: Unknown: DD090010180204F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"HOME-35F8_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000acf300183
                    Extra: Last beacon: 3952ms ago
                    IE: Unknown: 000D484F4D452D333546385F455854
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181FFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16060D1600000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180205F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"belkin.648"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002135d01176
                    Extra: Last beacon: 3820ms ago
                    IE: Unknown: 000A62656C6B696E2E363438
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010008
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001574b78d242
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 0505000100B406
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606030400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101800003A5000027A4000042435E0062322F00
                    IE: Unknown: 0B05060037127A
                    IE: Unknown: DD07000C4303000000
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"HOME-5D22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001574b7a5167
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 0009484F4D452D35443232
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 05050001002007
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880001DD10A5D20103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606030400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A5000027A4000042435E0062322F00
                    IE: Unknown: 0B05060037127A
                    IE: Unknown: DD07000C4303000000
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"HOME-0E94-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a3513a2180
                    Extra: Last beacon: 2696ms ago
                    IE: Unknown: 000D484F4D452D304539342D322E34
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 050400020000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0104
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFF7FFF00000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F050100000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001011049000600372A000120
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001574b7a5b49
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606030400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A5000027A4000042435E0062322F00
                    IE: Unknown: 0B05060037127A
                    IE: Unknown: DD07000C4303000000
          Cell 10 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Audacious-5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b3349a5f
                    Extra: Last beacon: 1076ms ago
                    IE: Unknown: 000B4175646163696F75732D35
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD270050F204104A000110104400010210470010864F2C8ADFFF8325EE9CCA9B0C486A36103C000103
                    IE: Unknown: DD090010180201F0010000
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A080400000000000000000000000000000000000000
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Seminoles"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a353bf7146
                    Extra: Last beacon: 756ms ago
                    IE: Unknown: 000953656D696E6F6C6573
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010101
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A88078CD8E0F2358103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040022127A
                    IE: Unknown: DD07000C4300000000
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a353bf7b88
                    Extra: Last beacon: 752ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040022127A
                    IE: Unknown: DD07000C4300000000
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"belkin.e12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023b82d9ce3
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000A62656C6B696E2E653132
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDAC0050F204104A0001101044000102103B0001031047001030A3D6076E38EDB69AC4275307ED52191021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303220763310240007332E30302E31301042000E31323233384746323332393334371054000800060050F20400011011001D42656C6B696E204E363030444220576972656C65737320526F7574657210080002200C103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"belkin.e12.guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023b82daaee
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 001162656C6B696E2E6531322E677565737473
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDAC0050F204104A0001101044000101103B0001031047001030A3D6076E38EDB69AC4275307ED52191021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303220763310240007332E30302E31301042000E31323233384746323332393334371054000800060050F20400011011001D42656C6B696E204E363030444220576972656C65737320526F7574657210080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


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
          Current Frequency:2.437 GHz (Channel 6)


##### modinfo #####


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
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


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
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


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    8.119947] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    8.382117] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.382334] rtlwifi: wireless switch is on
[   20.780284] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.784552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.982892] wlan0: authenticate with <MAC address removed>
[   24.004292] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.005822] wlan0: authenticated
[   24.006004] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   24.006309] wlan0: associate with <MAC address removed> (try 1/3)
[   24.012680] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   24.012788] wlan0: associated
[   24.012822] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.032116] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[   24.064554] wlan0: authenticate with <MAC address removed>
[   24.074642] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.076309] wlan0: authenticated
[   24.076501] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   24.078443] wlan0: associate with <MAC address removed> (try 1/3)
[   24.080956] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   24.081055] wlan0: associated
[  763.734759] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[  765.021005] wlan0: authenticate with <MAC address removed>
[  765.036844] wlan0: send auth to <MAC address removed> (try 1/3)
[  765.039308] wlan0: authenticated
[  765.039681] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  765.042295] wlan0: associate with <MAC address removed> (try 1/3)
[  765.044805] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  765.044903] wlan0: associated
[  924.698380] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[  924.735624] wlan0: authenticate with <MAC address removed>
[  924.745765] wlan0: send auth to <MAC address removed> (try 1/3)
[  924.747302] wlan0: authenticated
[  924.747746] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  924.751621] wlan0: associate with <MAC address removed> (try 1/3)
[  924.756626] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  924.756762] wlan0: associated
[ 1166.241444] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 1181.753617] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1189.381874] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1191.119898] wlan0: authenticate with <MAC address removed>
[ 1191.141558] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1191.146917] wlan0: authenticated
[ 1191.147090] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1191.150502] wlan0: associate with <MAC address removed> (try 1/3)
[ 1191.157002] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 1191.157099] wlan0: associated
[ 1191.157526] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1191.177181] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 1191.187652] wlan0: authenticate with <MAC address removed>
[ 1191.197900] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1191.213742] wlan0: authenticated
[ 1191.213953] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1191.214324] wlan0: associate with <MAC address removed> (try 1/3)
[ 1191.218084] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 1191.218273] wlan0: associated
[ 1300.897451] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1304.001141] wlan0: authenticate with <MAC address removed>
[ 1304.340124] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1304.341700] wlan0: authenticated
[ 1304.341895] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1304.344945] wlan0: associate with <MAC address removed> (try 1/3)
[ 1304.349194] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 1304.349302] wlan0: associated
[ 1458.746405] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1474.894091] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1476.604301] wlan0: authenticate with <MAC address removed>
[ 1476.620234] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1476.625841] wlan0: authenticated
[ 1476.626002] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1476.631674] wlan0: associate with <MAC address removed> (try 1/3)
[ 1476.634147] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 1476.634254] wlan0: associated
[ 1476.634692] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1476.656211] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 1476.692044] wlan0: authenticate with <MAC address removed>
[ 1476.702263] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1476.704653] wlan0: authenticated
[ 1476.705108] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1476.707752] wlan0: associate with <MAC address removed> (try 1/3)
[ 1476.710423] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 1476.710527] wlan0: associated


########## wireless info END ############
```

---

### Post by chili555 on 2014-07-31
Would you please change the encryption method on the router from TKIP to AES, reboot the router and give us your report?

[http://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](http://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)> TKIP uses the same underlying mechanism as WEP, and consequently is vulnerable to a number of similar attacks.

---

### Post by tgalati4 on 2014-07-31
Take the battery out of the laptop for an hour.  This will sometimes cause the wifi card to reload the firmware and reset the digital trims which can improve reception.  It's possible that you are too close to your wireless router and you need to lower transmission power or change channels due to interference from neighbors.  Install *wifi-radar* and count the number of wireless networks near you.

---

### Post by Nolster10 on 2014-07-31
Thanks for the help, I changed the encryption type and i'm going to leave the battery out now. I counted 14 networks on wifi radar, 8 of which including mine were on channel 6, if that has any correlation.

---

### Post by chili555 on 2014-07-31
I'd suggest, then, either 1 or 11; whichever has fewest neighbors. 

Any improvement?

---

### Post by Nolster10 on 2014-07-31
So far, so very good. Internet stability overall has seemed to improve, i'm not sure if this directly related but music applications don't stutter anymore and I have yet to be disconnected. Thank you guys for the help!

---

