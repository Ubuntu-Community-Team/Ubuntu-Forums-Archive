---
title: "WiFi not working on Atheros AR242x/AR542x in Acer Netbook"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by omegasaki on 2014-05-15
Hello,

Brand new to the world of Linux. Just wanted to try out a lightweight distro on a netbook I wasn't using.

I got it installed no problem but I can't get the wireless to work. 

Here's my wireless script:

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux mansacky-Aspire-one 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e00d]
    Kernel driver in use: ath5k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022f]
    Kernel driver in use: atl1c

##### lsusb #####

Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.158
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    DIRECT-roku-842: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2
    aminjon's Wi-Fi Network: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2
    LGNRD:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    SLKBP:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    ken:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    mimi:            Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    linksys_WPS_FF3A:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    4E7G3:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    habaobao:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP
    GDGY4:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Maxi's Web:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    4T4HN:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    GQRC1:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WEP
    SF8M2:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    NOFREEWIFIHERE:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    LD7MG:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    NETGEAR45:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    3DTY4:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    TFKW6:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    BPLSR:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    HZL3N:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    U10C022BC:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA
    beazly:          Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    shalom:          Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2

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

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007935b5c316e
                    Extra: Last beacon: 836ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 05050001000801
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860110BF483DE82F103C000101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1603000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504000E127A
                    IE: Unknown: DD07000C4307000000
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"LGNRD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b24c88395b
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00054C474E5244
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"aminjon's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006a1fb20dfd5
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0017616D696E6A6F6E27732057692D4669204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016B0B20
                    IE: Unknown: DD0E0017F2070001010668A86D654739
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-842"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f704fc7490
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000F4449524543542D726F6B752D383432
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706513220010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021200
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A7C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201102C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD7B0050F204104A0001101044000102103B0001031047001022210203040506070809B83E5922C8DF1021000842726F6164636F6D10230006536F66744150102400013010420001301054000800060050F20400011011000F4449524543542D726F6B752D383432100800020108103C0001011049000600372A000120
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"LD7MG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000070631c722d
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00054C44374D47
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"GDGY4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000aea3ff1351
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00054744475934
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 07 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"mimi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038d8c1d901
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00046D696D69
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000036127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B000103104700100000000000000001100008863B5EC41A1021001242656C6B696E20436F72706F726174696F6E1023000A46394B3130303220763210240007322E30302E30381042000E31323131333347433234363631341054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: 0706555320010B10
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NOFREEWIFIHERE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000470ab029fdd
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000E4E4F465245455749464948455245
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8B0050F204104A0001101044000102103B00010310470010933EF7EC87A35A7EBCEA4C60DED87868102100044E54475210230007574E52323030301024000256331042000C3463363064656438373836381054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020004103C0001011049000600372A000120
          Cell 09 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003f90b7b919c
                    Extra: Last beacon: 896ms ago
                    IE: Unknown: 00094E4554474541523435
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081500000000000000000000000000000000000000
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"4T4HN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e8aca094ec
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0005345434484E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 11 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"SLKBP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017058954315
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0005534C4B4250
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"4E7G3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000629196718b
                    Extra: Last beacon: 564ms ago
                    IE: Unknown: 00053445374733
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SF8M2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000035c47f906c
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00055346384D32
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"BPLSR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001106cde7a52
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000542504C5352
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"GQRC1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d12858575
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 00054751524331
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000

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

##### lsmod #####

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              545990  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F36818A2F0BCB2B0CC9BB8C
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512

##### modules #####

lp

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   14.123140] ath5k 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.123487] ath5k 0000:01:00.0: registered as 'phy0'
[   16.164600] ath: EEPROM regdomain: 0x65
[   16.164610] ath: EEPROM indicates we should expect a direct regpair map
[   16.164619] ath: Country alpha2 being used: 00
[   16.164624] ath: Regpair used: 0x65
[   16.242936] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   18.747531] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.750604] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

---

### Post by varunendra on 2014-05-16
Hi omegasaki, Welcome to the forums!

Please open a terminal (Ctrl-Alt-T) and try an old trick -
```
echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
.. and reboot.

Can you connect now? If not, please follow the instructions in this post to give us more info by running an experimental version of wireless_script : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Which country are you in? And which one is your Access-point in the listed ones? If it is one of those that appear to be using "WPA/WPA2" mixed mode, please change the encryption in the router/access-point to pure WPA2-PSK with AES (CCMP). No mixed mode, no TKIP. Reboot the router after saving the change.

---

### Post by omegasaki on 2014-05-16
Thanks for your reply.

After I ran that command and rebooted, I still wasn't able to connect. In network connections setting for the wireless, I left everything as is, set my SSID and password, selected infrastructure as mode, and selected the MAC address of my wlan interface.

To answer your questions, I'm in the US and my router is the ASUS RT-N56U. It's currently set to WPA2-Personal with AES.

With the script you linked me to, it did generate a .txt file but it was blank with a file size of 1KB.

---

### Post by Hadaka on 2014-05-16
Hi. please post the output of...
```
cat /etc/default/crda
lsmod
```
thanks.

---

### Post by omegasaki on 2014-05-16
```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=
```

```
Module                  Size  Used by
btusb                  27580  0 
dm_crypt               22622  0 
arc4                   12536  2 
snd_hda_codec_realtek    51029  1 
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
acer_wmi               31735  0 
snd_hwdep              13272  1 snd_hda_codec
sparse_keymap          13708  1 acer_wmi
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
coretemp               13195  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
ath5k                 134977  0 
videodev              108503  2 uvcvideo,videobuf2_core
ath                    23922  1 ath5k
joydev                 17101  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              545990  1 ath5k
snd_timer              28584  2 snd_pcm,snd_seq
serio_raw              13230  0 
lpc_ich                16864  0 
snd                    60871  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              409394  3 ath,ath5k,mac80211
soundcore              12600  1 snd
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  11 bnep,btusb,rfcomm
parport_pc             31981  0 
mac_hid                13037  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91033  0 
ahci                   25579  1 
libahci                26754  1 ahci
i915                  705396  2 
atl1c                  40949  0 
i2c_algo_bit           13197  1 i915
drm_kms_helper         46907  1 i915
drm                   243792  3 i915,drm_kms_helper
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi

```

---

### Post by Hadaka on 2014-05-16
thanks..please COPY and paste into a terminal..

#change your wireless regulatory domain from nothing to US
```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/" /etc/default/crda
```
BOOT
then please post..
```
cat /etc/default/crda
iw reg get
```
then do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
BOOT
any improvements?

---

### Post by omegasaki on 2014-05-18
&#65279;```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=US
```

The "iw reg get" says iw not currently installed. So I did "sudo apt-get install iw" and I get:
```
country 00:
   (2402 - 2472 @ 40), (3, 20)
   (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
   (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
   (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
   (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


```

After I entered the last code you gave me, nothing happened in the terminal so I rebooted and I still cannot connect.

---

### Post by Hadaka on 2014-05-18
hi, COPY and paste...
```
sudo apt-get update
sudo apt-get upgrade
```
BOOT
```
sudo sed -i "s/REGDOMAIN=US/REGDOMAIN=/" /etc/default/crda
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/" /etc/default/crda
sudo iw reg set US
```
BOOT
post the outout of,,
```
cat /etc/default/crda
iw reg get
```
thanks.

---

### Post by omegasaki on 2014-05-19
```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=US


```

```
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


```

---

### Post by varunendra on 2014-05-20
> **omegasaki said:**
> With the script you linked me to, it did generate a .txt file but it was blank with a file size of 1KB.

Please try again carefully, and if it again generates a blank file, please post the entire output that shows up on the terminal while running the script. It is an experimental script yet, but I can't imagine why it would generate a blank file.

---

### Post by omegasaki on 2014-05-22
I've tried three times with the same result, but here's the output from terminal when it's executed:

```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-05-22 23:19:24--  https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 75.101.163.157
Connecting to dl.dropbox.com (dl.dropbox.com)|75.101.163.157|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script [following]
--2014-05-22 23:19:24--  https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 23.21.107.15, 54.225.180.56, 54.225.207.37, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.21.107.15|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15521 (15K) [text/plain]
Saving to: &#8216;wireless_script&#8217;

100%[======================================>] 15,521      --.-K/s   in 0.001s  

Last-modified header missing -- time-stamps turned off.
2014-05-22 23:19:25 (14.2 MB/s) - &#8216;wireless_script&#8217; saved [15521/15521]



        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****
  
  If this takes more than 1 minute, you may abort the script by pressing
  "Ctrl+Z" on your keyboard.
  
  (Type your Login Password when asked, then press 'Enter')

sed: -e expression #1, char 782: extra characters after command


    ########################################################################

    DONE! All results saved in -

         File Name:     "wireless-info.txt" 
         Directory:     "/home/mansacky"

    Please upload the above file or its contents where you are seeking help.

    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------

    ########################################################################


```

---

### Post by omegasaki on 2014-05-22
I've tried three times with the same result, but here's the output from terminal when it's executed:

```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-05-22 23:19:24--  https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 75.101.163.157
Connecting to dl.dropbox.com (dl.dropbox.com)|75.101.163.157|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script [following]
--2014-05-22 23:19:24--  https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 23.21.107.15, 54.225.180.56, 54.225.207.37, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.21.107.15|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15521 (15K) [text/plain]
Saving to: ‘wireless_script’

100%[======================================>] 15,521      --.-K/s   in 0.001s  

Last-modified header missing -- time-stamps turned off.
2014-05-22 23:19:25 (14.2 MB/s) - ‘wireless_script’ saved [15521/15521]



        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****
  
  If this takes more than 1 minute, you may abort the script by pressing
  "Ctrl+Z" on your keyboard.
  
  (Type your Login Password when asked, then press 'Enter')

sed: -e expression #1, char 782: extra characters after command


    ########################################################################

    DONE! All results saved in -

         File Name:     "wireless-info.txt" 
         Directory:     "/home/mansacky"

    Please upload the above file or its contents where you are seeking help.

    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------

    ########################################################################


```

---

### Post by Hadaka on 2014-05-23
hi, it look like it saved the wireless script..

2014-05-22 23:19:25 (14.2 MB/s) - &#8216;wireless_script&#8217; saved [15521/15521] <<<------
[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]
open a terminal and do..
lower case LS
```
ls
``` 
look for 
wireless-info.txt[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]  <<<<0000------
copy and paste here.
thanks.

---

### Post by omegasaki on 2014-05-23
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

mansacky-Aspire-one 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Memory : 2006 MB
Uptime : 10:37:44 up 4 min,  2 users,  load average: 0.24, 0.36, 0.19


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e00d]
    Kernel driver in use: ath5k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022f]
    Kernel driver in use: atl1c


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no
1: acer-bluetooth: Bluetooth        no            no
2: phy0: Wireless LAN               no            no
3: hci0: Bluetooth                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              545990  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath5k         (3): fastchanswitch=N | nohwcrypt=Y | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | atl1c  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.158
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    DIRECT-roku-842: Infra, <MAC C-05 DIRECT-roku-842>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    aminjon's Wi-Fi Network: Infra, <MAC C-01 aminjon's Wi-Fi Network>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    LGNRD:           Infra, <MAC C-04 LGNRD>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    SF8M2:           Infra, <MAC C-NA SF8M2 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    ken:             Infra, <MAC C-06 ken>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    B2PCJ:           Infra, <MAC C-NA B2PCJ 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    BPLSR:           Infra, <MAC C-15 BPLSR>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    LD7MG:           Infra, <MAC C-NA LD7MG 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2
    SLKBP:           Infra, <MAC C-03 SLKBP>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA2
    4T4HN:           Infra, <MAC C-NA 4T4HN 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 7 WPA2
    habaobao:        Infra, <MAC C-12 habaobao>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WEP
    GQRC1:           Infra, <MAC C-13 GQRC1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WEP
    mimi:            Infra, <MAC C-10 mimi>, Freq 2417 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    apt3O:           Infra, <MAC C-08 apt3O>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    GDGY4:           Infra, <MAC C-09 GDGY4>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    P5F49:           Infra, <MAC C-NA P5F49 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA2
    4E7G3:           Infra, <MAC C-07 4E7G3>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP
    Maxi's Web:      Infra, <MAC C-NA Maxi's Web 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    9Y3X5:           Infra, <MAC C-NA 9Y3X5 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    MTA5915:         Infra, <MAC C-NA MTA5915 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Mikhail Iskhakov's Network: Infra, <MAC C-11 Mikhail Iskhakov's Network>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.365/0.386/0.408/0.029 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.081/0.082/0.083/0.001 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 aminjon's Wi-Fi Network>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"aminjon's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000033b7335c9e
                    Extra: Last beacon: 14028ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 >
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000829a54611e0
                    Extra: Last beacon: 612ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 SLKBP>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SLKBP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000206a1a852b2
                    Extra: Last beacon: 14028ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 LGNRD>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"LGNRD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001489694e9f2
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 DIRECT-roku-842>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-842"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000839e010ed0
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 ken>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ken"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ae77d885
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 4E7G3>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"4E7G3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007400977022
                    Extra: Last beacon: 76ms ago
          Cell 08 - Address: <MAC C-08 apt3O>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"apt3O"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ef443ddbf6
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 GDGY4>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"GDGY4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000144ed0196d2
                    Extra: Last beacon: 14028ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 mimi>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"mimi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000424e991ad3
                    Extra: Last beacon: 14528ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 Mikhail Iskhakov's Network>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Mikhail Iskhakov's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005b1b926991
                    Extra: Last beacon: 14388ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 habaobao>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"habaobao"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000013b105971
                    Extra: Last beacon: 14380ms ago
          Cell 13 - Address: <MAC C-13 GQRC1>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"GQRC1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001dc697b9ed
                    Extra: Last beacon: 14028ms ago
          Cell 14 - Address: <MAC C-14 HZL3N>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HZL3N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c255ece199
                    Extra: Last beacon: 14072ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 BPLSR>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"BPLSR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a6b5ee76b0
                    Extra: Last beacon: 14028ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 PJKB9>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"PJKB9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000426e39c4c2
                    Extra: Last beacon: 424ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath5k.conf        : options ath5k nohwcrypt=Y
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=e849eab5-59e5-4f30-a4ac-4ccca288527b ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.828731] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.829501] audit: initializing netlink socket (disabled)
[    3.147463] wmi: Mapper loaded
[   14.056223] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.834581] ath5k 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.834930] ath5k 0000:01:00.0: registered as 'phy0'
[   15.971807] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.179394] acer_wmi: Function bitmap for Communication Device: 0x11
[   16.179420] acer_wmi: Brightness must be controlled by acpi video driver
[   16.669723] ath: EEPROM regdomain: 0x65
[   16.669734] ath: EEPROM indicates we should expect a direct regpair map
[   16.669744] ath: Country alpha2 being used: 00
[   16.669749] ath: Regpair used: 0x65
[   16.779117] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   19.236261] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.243365] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

---

### Post by varunendra on 2014-05-26
Sorry for the delayed response.. was too busy in my office work..

Just noticed the thread has prefix "Lubuntu", which has recently been facing a bug with Network Manager. Do you get "nm-applet" icon at all? Your report is almost same as another Lubuntu thread I just replied, and so the suggestion is also the same.

Please check the "Edit" part of this post first : [http://ubuntuforums.org/showpost.php?p=13033452](http://ubuntuforums.org/showpost.php?p=13033452)

If that is okay, try the other suggestions from the same post.

---

### Post by omegasaki on 2014-05-26
It worked! Finally! Thank you so much! I was just about to give up too.

You weren't specific where to press Alt+F2, so I tried that in the desktop area but nothing happened. Then I opened a terminal and typed nm-applet. A network icon popped up on the bottom right and when I clicked it I saw the list of available networks. I added mine and it connected. I also saw that notification pop up on the top right.

Again, thank you! And thanks to Hadaka for helping out as well.

---

### Post by varunendra on 2014-05-27
Good to know that nm-applet was all that you needed. :)
> **omegasaki said:**
> You weren't specific where to press Alt+F2, so I tried that in the desktop area but nothing happened..
Not only Alt-F2, but there are many discrepancies in my description and the actual status/location/behaviour of things in Lubuntu. I had given the steps as per default Ubuntu, and I have absolutely no idea how different they are in Lubuntu.

Fortunately for you, the original poster "bill" on the thread I linked to has posted a very detailed description of the discrepancies and the ways around them to achieve the goal. Particularly this link is quite useful for you to avoid terminal to run nm-applet : [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

If this solves the problem permanently, please mark the thread as [SOLVED] to help others. Thanks!

---

