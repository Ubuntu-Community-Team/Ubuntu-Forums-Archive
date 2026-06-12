---
title: "Intel 6200-AGN / Ubuntu 13.10 / Lenovo x201s"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by Metaphorosis on 2014-02-15
I can see wireless networks, but generally can't connect. I did manage to connect to one neighbourhood network (an N network like my own), and previously could occasionally connect to mine at low speed (802.11N).

I had this same issue a year ago, and tried all sorts of things that didn't work. I tried again with Ubuntu 13.10 and Mint Cinnamon 16. One suggestion was to enable WMM on my router, but I don't seem to have such a setting (though I can set specific bandwidth rules). Finally, I tried a [script]("http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385") found on these forums, which generated the below information. I ran it in Cinnamon, but I presume the result is the same.

My network is 'Latskan'. The other one I was able to connect to is SBB Zona

```

*************** info trace ***************

***** uname -a *****

Linux mint 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    LinuxMint
Description:    Linux Mint 16 Petra
Release:    16
Codename:    petra

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
    Subsystem: Lenovo Device [17aa:2153]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1311]
    Kernel driver in use: iwlwifi

***** lsusb *****

Bus 002 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. RTS5159 Card Reader Controller
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 004: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 003: ID 0781:5202 SanDisk Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

iwldvm                237440  0 
mac80211              596969  1 iwldvm
iwlwifi               165398  1 iwldvm
cfg80211              479757  3 iwlwifi,mac80211,iwldvm

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Latskan:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    sbb.mrakovic:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Branko:          Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 49 WPA2
    CENTRAL PARK RESIDENCE1: Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Suminona:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    maart studio:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    CENTRAL PARK RESIDENCE: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    TP-LINK_ACBC44:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    meduza:          Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39
    SBB Zona:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    PTICA:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    HERMES:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    4819de:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    UniFi:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    tikica555:       Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    SBB Zona:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29
    magic:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA
    Minic:           Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 22 WPA
    UniFi:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Latskan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000168d904d13
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00074C6174736B616E
                    IE: Unknown: 010882848B968C9298A4
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051300000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700106304125310192006122800E0612FA2E31021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020086
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120
          Cell 02 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Branko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000039917f0d65
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00064272616E6B6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34090F0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000101103B0001031047001000000000000010000000B0487AB524F41021000754502D4C494E4B10230009544C2D57523834314E10240007362E302F372E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"SBB Zona"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007e0189507
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0008534242205A6F6E61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0C1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD2A000C42000000011E00100000006618050000303030433432364230423430000000000000000005029E09
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UniFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007e018a015
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0005556E694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0C1003FF00000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD2A000C42000000011E00140000006618050000303030433432364230423430000000000000000005029E09
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"sbb.mrakovic"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001833592c990
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000C7362622E6D72616B6F766963
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010312C8E58A3BF2F4C2245182D191C2F0F10210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006653539653961100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"magic"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000015323f443
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00056D61676963
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100000259CAFCC9F102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30311042000C4A555430304A4133363135331054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"maart studio"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001361fa927c
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000C6D616172742073747564696F
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
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F0280000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"CENTRAL PARK RESIDENCE1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000047e1a75a4d2
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 001743454E5452414C205041524B205245534944454E434531
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1604051700000000000000000000000000000000000000
                    IE: Unknown: 341604051700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 09 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"PTICA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e550059d13
                    Extra: Last beacon: 14988ms ago
                    IE: Unknown: 00055054494341
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD9E0050F204104A00011010440001011057000101103B000103104700100000000000001000000064700279E3101021000754502D4C494E4B10230009544C2D57523734304E10240003342E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 10 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"CENTRAL PARK RESIDENCE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ceda155302
                    Extra: Last beacon: 18324ms ago
                    IE: Unknown: 001643454E5452414C205041524B205245534944454E4345
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0506000101200008
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180214F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Minic"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c4bd00419f
                    Extra: Last beacon: 18276ms ago
                    IE: Unknown: 00054D696E6963
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602050700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050002167A12
                    IE: Unknown: DD1E00904C330E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"SBB Zona"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007e0180f0b
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0008534242205A6F6E61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0C1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: DD2A000C42000000011E00100000006618050000303030433432364230423432000000000000000005028509
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
          Cell 13 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"UniFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007e01829d6
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0005556E694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0C1003FF00000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: DD2A000C42000000011E00140000006618050000303030433432364230423432000000000000000005028509
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
          Cell 14 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Suminona"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005f4bb8ef
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000853756D696E6F6E61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD810050F204104A0001101044000102103B0001031047001000000000000010000000940C6DF75EB01021000754502D4C494E4B10230009544C2D57523834314E10240003352E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HERMES"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000185de8e47cc
                    Extra: Last beacon: 2976ms ago
                    IE: Unknown: 00064845524D4553
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 05040001003A
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 16 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"4legal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000044659f93185
                    Extra: Last beacon: 2972ms ago
                    IE: Unknown: 0006346C6567616C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706435320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 0505000100E006
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010039127A
                    IE: Unknown: DD07000C4307000000
          Cell 17 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"meduza"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a65cc5141
                    Extra: Last beacon: 2944ms ago
                    IE: Unknown: 00066D6564757A61
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706435320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010060
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160A070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040022127A
                    IE: Unknown: DD07000C4307000000


***** resolv.conf *****


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

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     189D6366522149BFF40DA25
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B3EF32124305F5D1F6E94A5
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
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
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


***** udev rules *****

# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4239 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   24.257029] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   24.257186] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[   24.600181] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   24.867138] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   24.867143] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   24.867145] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   24.867146] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   24.867149] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   24.867324] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   24.999003] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   26.282783] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   26.290126] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[   26.502026] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   26.509736] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[   26.586371] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.586739] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.872366] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3

****************** done ******************


```

---

### Post by chili555 on 2014-02-15
As luck would have it, the technician with the most Intel experience and who is typing right now from a 6200 that connects perfectly at N speeds is available now. No waiting. Your table is ready.

The driver iwlwifi has notorious difficulty with N speeds. It often won't connect at all and then, if it does, won't pass traffic at all. I have come to believe it is related to the driver/hardware/router combination. I am also convinced that the router manufacturers and Intel engage in a bit of finger-pointing about this. I also know that Intel has wireless issues in Windows, too.

Let's start easy and work our way up. Please open a terminal and do:```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi  [COLOR="#FF0000"]<--may already be removed, just continue[/COLOR]
sudo modprobe iwlwifi 11n_disable=1
```If this helps, we can amend a file and make it persistent. If not, there are other increasingly complex things to try, some of them in the router.

---

### Post by Metaphorosis on 2014-02-16
> **chili555 said:**
> As luck would have it, the technician with the most Intel experience and who is typing right now from a 6200 that connects perfectly at N speeds is available now. No waiting. Your table is ready.


In that case, I'd like to order the Easy Connection special, with all trimmings.;)

I followed instructions. After the second line, I got:
```
Error: missing module name.
FATAL: Error running remove command for iwlwifi

```
I continued as directed.

Unfortunately, no change in connectivity. I was still able to connect to SBB Zona, and unable to connect to Latskan.

FYI - I'm running Mint from a USB as a Live user via YUMI multi-boot (with a persistent storage area), in case that matters. Not entirely sure that commands such as above would persist from one session to another.

---

### Post by chili555 on 2014-02-16
We'll keep trying, then.```
sudo modprobe -r iwldvm
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N 
```Then I'd check your regulatory domain (read: country code):```
iw reg get
```If you see something like:> country 00In this context, 00 means one-size-maybe-fits-all just like my old orange jumpsuit. Many have better luck setting the code explicitly. Find your code here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then, set the code explicitly. For instance, if your country is Iceland:```
sudo iw reg set IS
```If we find that some or all of these settings help you connect, we will amend a couple of files to make them permanent.

---

### Post by Metaphorosis on 2014-02-16
1. I've shifted the attempts to Ubuntu 13.10 (from Mint), but still as a Live user from flash drive. Just in case, I
 a) tested connections again with the same result - can't connect to my network, can connect to the neighbours (though it's useless in practice, since it requires a login for internet access).
 b) tried the previous instructions again - same result.

2. I tried the new instructions. I entered both commands in sequence, and tested connection only after entering both. No change.

3. The result of the country code query was:

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

4. I assume the country code refers to physical location, but for safety, I tried both physical location (Serbia) and source of the computer (US - in the sense it was sold there, not made there), and then back to Serbia. No change.

---

### Post by chili555 on 2014-02-16
> I tried both physical location (Serbia) and source of the computer (US - in the sense it was sold there, not made there), and then back to Serbia. No change. I think a significant factor is where the router was sold. If, for instance, US, then you might try:```
sudo iw reg set US
```I gather you tried US already with no success, but is that where the router was sold?

What is happening with Network Manager?```
cat /var/log/syslog | grep -e iwl -e etwork | tail -n20
```

Do you have administrative privileges for the router? We mat need to try a couple of settings there.

---

### Post by Metaphorosis on 2014-02-17
The router was almost certainly sold in Serbia (it was provided by my landlord, so I'm not entirely sure). It's a relatively generic model (Gembird NSW-R3), but works well enough for my Windows PCs. I do have administrative privileges.

The Network Manager result was:

> Feb 17 10:17:14 it NetworkManager[2813]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Feb 17 10:17:14 it NetworkManager[2813]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 17 10:17:14 it NetworkManager[2813]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 17 10:17:14 it NetworkManager[2813]: <info> (wlan0): bringing up device.
Feb 17 10:17:14 it kernel: [   21.796590] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
Feb 17 10:17:14 it kernel: [   21.808056] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
Feb 17 10:17:15 it kernel: [   22.021585] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
Feb 17 10:17:15 it kernel: [   22.028610] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
Feb 17 10:17:15 it NetworkManager[2813]: <info> (wlan0): preparing device.
Feb 17 10:17:15 it NetworkManager[2813]: <info> (wlan0): deactivating device (reason 'managed') [2]
Feb 17 10:17:15 it NetworkManager[2813]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Feb 17 10:17:15 it NetworkManager[2813]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Feb 17 10:17:15 it NetworkManager[2813]: <info> wpa_supplicant started
Feb 17 10:17:15 it NetworkManager[2813]: <info> (wlan0) supports 5 scan SSIDs
Feb 17 10:17:15 it NetworkManager[2813]: <warn> Trying to remove a non-existant call id.
Feb 17 10:17:15 it NetworkManager[2813]: <info> (wlan0): supplicant interface state: starting -> ready
Feb 17 10:17:15 it NetworkManager[2813]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 17 10:17:15 it NetworkManager[2813]: <info> (wlan0): supplicant interface state: ready -> inactive
Feb 17 10:17:15 it NetworkManager[2813]: <info> (wlan0) supports 5 scan SSIDs
Feb 17 10:17:18 it NetworkManager[2813]: <warn> Couldn't retrieve BSSID properties: failed to parse RSN IE.



---

### Post by chili555 on 2014-02-17
I'd try the country code for Serbia:```
sudo iw reg set RS
```I am troubled by this:> <warn> Couldn't retrieve BSSID properties: failed to parse RSN IE.RSN is a part of the WPA2 authentication protocol: [http://en.wikipedia.org/wiki/IEEE_802.11i-2004](http://en.wikipedia.org/wiki/IEEE_802.11i-2004)> The RSN is a security network that only allows the creation of robust security network associations (RSNAs), which are a type of association used by a pair of stations (STAs) if the procedure to establish authentication or association between them includes the 4-Way Handshake.Googling that exact phrase yields nothing that's helpful to me. 

I suggest you enter the router's administration pages and set the channel width to 20 MHz, set the encryption method to WPA2-AES (not the dreaded and troublesome WPA mixed mode) and I'd disable WPS. Make certain that MAC address filtering is off. I'd disable WDS. Apply the changes and reboot the router. Now try to connect again. Is the RSN warning still present after the timestamp *Feb 17 10:17:18 *?

---

### Post by Metaphorosis on 2014-02-21
Thanks!:p

It took me a while, but I finally did get a chance to try this. I followed all your instructions:
 - channel width to 20 MHz (from 40)
 - encryption was already WPA2-AES
 - WPS disabled
 - MAC filtering was already off
 - WDS was already disabled.

I rebooted the router, started Ubuntu, and - I connected! Started Mint, and it worked just as well. For the record, the output of the command is now:

it@it:~$ cat /var/log/syslog | grep -e iwl -e etwork | tail -n20
Feb 21 19:15:58 it NetworkManager[2734]: <info> (wlan0): using nl80211 for WiFi device control
Feb 21 19:15:58 it kernel: [   27.428166] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
Feb 21 19:15:58 it kernel: [   27.428365] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
Feb 21 19:15:58 it NetworkManager[2734]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Feb 21 19:15:58 it NetworkManager[2734]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 21 19:15:58 it NetworkManager[2734]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 21 19:15:58 it NetworkManager[2734]: <info> (wlan0): bringing up device.
Feb 21 19:15:59 it kernel: [   27.639049] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
Feb 21 19:15:59 it kernel: [   27.639246] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
Feb 21 19:15:59 it NetworkManager[2734]: <info> (wlan0): preparing device.
Feb 21 19:15:59 it NetworkManager[2734]: <info> (wlan0): deactivating device (reason 'managed') [2]
Feb 21 19:15:59 it NetworkManager[2734]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Feb 21 19:15:59 it NetworkManager[2734]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Feb 21 19:15:59 it NetworkManager[2734]: <info> wpa_supplicant started
Feb 21 19:15:59 it NetworkManager[2734]: <info> (wlan0) supports 5 scan SSIDs
Feb 21 19:15:59 it NetworkManager[2734]: <warn> Trying to remove a non-existant call id.
Feb 21 19:15:59 it NetworkManager[2734]: <info> (wlan0): supplicant interface state: starting -> ready
Feb 21 19:15:59 it NetworkManager[2734]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 21 19:15:59 it NetworkManager[2734]: <info> (wlan0): supplicant interface state: ready -> inactive
Feb 21 19:15:59 it NetworkManager[2734]: <info> (wlan0) supports 5 scan SSIDs


Thanks very much for taking the time to help me out with this. I'm looking forward to finally being able to try out Ubuntu on this machine in a fully connected state. If there's a way on this forum to give you kudos, I'll find it.

Morris

---

