---
title: "Woke up this morning and wireless doesn't work"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by GammaPoint on 2013-10-21
I'm running the 12.04 Xubuntu LTS on a Thinkpad T61. For a year or so now I've occasionally had wireless problems (in that it will have difficulty connecting to the router). When it first started occurring to me I'd reboot and within 1-3 reboots it would just work again. After awhile, I realized that if I disabled and then re-enabled wireless that it seemed to do the same thing, and then it would connect.

Flash forward to this morning, when none of these options are working. It just can't connect to my wireless router for some reason. I just connected it with the cable and it works fine though.
Any thoughts to the cause of the problem? Or how to determine if it's a hardware or software issue? My wife's MACs are connected to the internet wireless just fine atm.

Perhaps in getting some expert advice here rather than my 'hope this works' workarounds, I'll be able to fix the problem for good.

I imagine you need some more information, so I'll try to post some of the output I see others asking for in similar threads:

```

$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)

```

```

$ uname -r 
3.2.0-54-generic

```

If you need any other info please let me know. Thanks in advance for the assistance!

Edit: Ran the 'wireless script' from the post [http://ubuntuforums.org/showthread.php?t=2182286]("http://ubuntuforums.org/showthread.php?t=2182286"). The output of this script is:

```


*************** info trace ***************

***** uname -a *****

Linux babybear 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:09:12 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
	Subsystem: Lenovo ThinkPad T61/R61 [17aa:20b9]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
	Subsystem: Intel Corporation Device [8086:1010]
	Kernel driver in use: iwl3945

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:129e Apple, Inc. iPod Touch 4.Gen

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

iwl3945                73145  0 
iwl_legacy             71187  1 iwl3945
mac80211              436493  2 iwl3945,iwl_legacy
cfg80211              178877  3 iwl3945,iwl_legacy,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HOME-CB33:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    Shen:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Realworlddotcom: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    SKC:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Lightning:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    magarule_EXT:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    mikellen:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA
    HOME-3353:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    midnight shade:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    HOME-6042:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Bear Den:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA2
    Bunnyfuncy:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    FSJK:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    I'm Under Your Bed: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    DraggaFogarty:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    11FX05096587:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WEP
    307eberkely:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    CoxWiFi:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    Poopsicles:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    CableWiFi:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    BrooklynBamboo:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    muchi123:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    myLGNet:         Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WEP
    HOME-E152:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    HOME-D8E2:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    nacheeee:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    HOME-A634:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    SANDERS:         Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 14 WPA2
    VM__NET:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2
    HOME-E497:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Penny:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP
    snyder01:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WEP


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- VPN:  [PIA (US EAST)] --------------------------------------------------------
  State:             connected
  Default:           no

  Message:



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

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
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Realworlddotcom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ffe019d80
                    Extra: Last beacon: 1972ms ago
                    IE: Unknown: 000F5265616C776F726C64646F74636F6D
                    IE: Unknown: 010882848B968C129824
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
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34020D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16020D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B0001031047001000000000000010000000E0469A426E151021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"midnight shade"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b2d79a2f0
                    Extra: Last beacon: 1800ms ago
                    IE: Unknown: 000E6D69646E69676874207368616465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201100C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9D0050F204104A00011010440001021041000100103B000103104700100000000000000001000308863BFC54061021001242656C6B696E20436F72706F726174696F6E1023000946394B31303031763410240007342E30302E30361042000E31323132313747423433343437321054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020080
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"11FX05096587"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002802f3cd333
                    Extra: Last beacon: 1804ms ago
                    IE: Unknown: 000C313146583035303936353837
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"HOME-CB33"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003726db61ef5
                    Extra: Last beacon: 1624ms ago
                    IE: Unknown: 0009484F4D452D43423333
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B0001031047001044E783B07077370C56770E8DF15B12281021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180203F03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Shen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000136e6d74c1f
                    Extra: Last beacon: 1640ms ago
                    IE: Unknown: 00045368656E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"HOME-3353"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fcc3715ac
                    Extra: Last beacon: 1636ms ago
                    IE: Unknown: 0009484F4D452D33333533
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B00010310470010E0D240D9470BA3B18DAA52E947FEECA91021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"Bear Den"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001254b705d
                    Extra: Last beacon: 1780ms ago
                    IE: Unknown: 0008426561722044656E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"307eberkely"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f420ac410a
                    Extra: Last beacon: 2120ms ago
                    IE: Unknown: 000B333037656265726B656C79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8A0050F204104A00011010440001021041000100103B0001031047001094AE65C91B96B21A30BE0E9944B62E2D1021000D4E4554474541522C20496E632E1023000857475236313476381024000857475236313476381042000538333235381054000800060050F20400011011001657475236313476382028576972656C65737320415029100800020084
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"I'm Under Your Bed"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010bd1be4139
                    Extra: Last beacon: 1932ms ago
                    IE: Unknown: 001249276D20556E64657220596F757220426564
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 0504000100B0
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880E8892C5D1420103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040043127A
                    IE: Unknown: DD07000C4303000000
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Lightning"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b2438215c0b
                    Extra: Last beacon: 1620ms ago
                    IE: Unknown: 00094C696768746E696E67
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E95
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD0E0017F2070001010628CFDAB19045
          Cell 11 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"FSJK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000021c3a5718e
                    Extra: Last beacon: 2276ms ago
                    IE: Unknown: 000446534A4B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"magarule_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000564142ef
                    Extra: Last beacon: 2152ms ago
                    IE: Unknown: 000C6D61676172756C655F455854
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010bd1be4b8b
                    Extra: Last beacon: 1928ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040043127A
                    IE: Unknown: DD07000C4303000000
          Cell 14 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"HOME-6042"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000032004fb224
                    Extra: Last beacon: 1900ms ago
                    IE: Unknown: 0009484F4D452D36303432
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 05040001000E
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880001DD6EA6040103C0001011049000600372A000120
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606030100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500006C127A
                    IE: Unknown: DD07000C4303000000
          Cell 15 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000032004983b8
                    Extra: Last beacon: 2304ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606030100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500006C127A
                    IE: Unknown: DD07000C4303000000
          Cell 16 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"SKC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010bca880df8
                    Extra: Last beacon: 1640ms ago
                    IE: Unknown: 0003534B43
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050030127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880E8892C5F681010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 17 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"HOME-A634"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000011f580634f
                    Extra: Last beacon: 1616ms ago
                    IE: Unknown: 0009484F4D452D41363334
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B00010310470010070D6860AC251032EF64729E5F6C849B1021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 18 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"muchi123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000201ee667183
                    Extra: Last beacon: 1612ms ago
                    IE: Unknown: 00086D75636869313233
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"mikellen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001b27cc22e56
                    Extra: Last beacon: 2192ms ago
                    IE: Unknown: 00086D696B656C6C656E
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 20 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"VM__NET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001622348919d
                    Extra: Last beacon: 2224ms ago
                    IE: Unknown: 0007564D5F5F4E4554
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081500000000000000000000000000000000000000
          Cell 21 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"CableWiFi"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000596b360180
                    Extra: Last beacon: 2180ms ago
                    IE: Unknown: 00094361626C6557694669
                    IE: Unknown: 01088B960C1218243048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 070655534F010D1E
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1AAD0103FFF0E000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201010D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F


***** resolv.conf *****

nameserver 127.0.0.1
search hsd1.ma.comcast.net

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

filename:       /lib/modules/3.2.0-54-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     301B04B4010DED41B0830D0
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
intree:         Y
vermagic:       3.2.0-54-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.2.0-54-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     D949E7611CAAE3FC9AEDE7D
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-54-generic SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


***** udev rules *****

# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   20.749484] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   20.749487] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   20.749547] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.749562] iwl3945 0000:03:00.0: setting latency timer to 64
[   20.857861] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   20.857864] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   20.858013] iwl3945 0000:03:00.0: irq 48 for MSI/MSI-X
[   20.896742] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.303365] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   22.376309] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.376549] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.015405] wlan0: authenticate with <MAC address removed> (try 1)
[   29.017329] wlan0: authenticated
[   29.023672] wlan0: associate with <MAC address removed> (try 1)
[   29.026109] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   29.026112] wlan0: associated
[   29.027634] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.363612] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   32.995908] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   35.462603] wlan0: authenticate with <MAC address removed> (try 1)
[   35.464435] wlan0: authenticated
[   35.464566] wlan0: associate with <MAC address removed> (try 1)
[   35.467009] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   35.467012] wlan0: associated
[   39.438114] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   41.914555] wlan0: authenticate with <MAC address removed> (try 1)
[   41.916441] wlan0: authenticated
[   41.916597] wlan0: associate with <MAC address removed> (try 1)
[   41.919142] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   41.919145] wlan0: associated
[   45.888918] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   48.355527] wlan0: authenticate with <MAC address removed> (try 1)
[   48.358718] wlan0: authenticated
[   48.358809] wlan0: associate with <MAC address removed> (try 1)
[   48.361164] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   48.361170] wlan0: associated
[   52.324580] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   54.802978] wlan0: authenticate with <MAC address removed> (try 1)
[   54.807151] wlan0: authenticated
[   54.807260] wlan0: associate with <MAC address removed> (try 1)
[   54.809742] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   54.809745] wlan0: associated
[   58.774293] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   61.258917] wlan0: authenticate with <MAC address removed> (try 1)
[   61.260801] wlan0: authenticated
[   61.260932] wlan0: associate with <MAC address removed> (try 1)
[   61.263287] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   61.263291] wlan0: associated
[   65.224159] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   67.704909] wlan0: authenticate with <MAC address removed> (try 1)
[   67.707885] wlan0: authenticated
[   67.708110] wlan0: associate with <MAC address removed> (try 1)
[   67.710494] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   67.710497] wlan0: associated
[   71.674011] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   74.139614] wlan0: authenticate with <MAC address removed> (try 1)
[   74.142157] wlan0: authenticated
[   74.142289] wlan0: associate with <MAC address removed> (try 1)
[   74.146397] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   74.146400] wlan0: associated
[   78.113993] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   80.596142] wlan0: authenticate with <MAC address removed> (try 1)
[   80.602434] wlan0: authenticated
[   80.602546] wlan0: associate with <MAC address removed> (try 1)
[   80.605082] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   80.605085] wlan0: associated
[   84.573747] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  106.123459] wlan0: authenticate with <MAC address removed> (try 1)
[  106.125277] wlan0: authenticated
[  106.125435] wlan0: associate with <MAC address removed> (try 1)
[  106.130974] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  106.130978] wlan0: associated
[  110.093209] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  112.568077] wlan0: authenticate with <MAC address removed> (try 1)
[  112.569876] wlan0: authenticated
[  112.569999] wlan0: associate with <MAC address removed> (try 1)
[  112.574236] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  112.574240] wlan0: associated
[  116.544340] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  119.012224] wlan0: authenticate with <MAC address removed> (try 1)
[  119.016253] wlan0: authenticated
[  119.016954] wlan0: associate with <MAC address removed> (try 1)
[  119.020329] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  119.020338] wlan0: associated
[  122.982905] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  125.452540] wlan0: authenticate with <MAC address removed> (try 1)
[  125.459834] wlan0: authenticated
[  125.460356] wlan0: associate with <MAC address removed> (try 1)
[  125.466572] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  125.466581] wlan0: associated
[  129.432737] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  131.919811] wlan0: authenticate with <MAC address removed> (try 1)
[  131.922289] wlan0: authenticated
[  131.922482] wlan0: associate with <MAC address removed> (try 1)
[  131.924805] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  131.924810] wlan0: associated
[  135.892601] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  138.367366] wlan0: authenticate with <MAC address removed> (try 1)
[  138.369230] wlan0: authenticated
[  138.376054] wlan0: associate with <MAC address removed> (try 1)
[  138.378832] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  138.378841] wlan0: associated
[  142.342841] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  144.814630] wlan0: authenticate with <MAC address removed> (try 1)
[  144.816444] wlan0: authenticated
[  144.817097] wlan0: associate with <MAC address removed> (try 1)
[  144.819871] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  144.819881] wlan0: associated
[  148.783053] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  151.255302] wlan0: authenticate with <MAC address removed> (try 1)
[  151.259548] wlan0: authenticated
[  151.260226] wlan0: associate with <MAC address removed> (try 1)
[  151.267873] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  151.267882] wlan0: associated
[  155.232188] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  157.696408] wlan0: authenticate with <MAC address removed> (try 1)
[  157.700058] wlan0: authenticated
[  157.701582] wlan0: associate with <MAC address removed> (try 1)
[  157.704342] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  157.704345] wlan0: associated
[  161.671973] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  169.570854] wlan0: authenticate with <MAC address removed> (try 1)
[  169.572693] wlan0: authenticated
[  169.572992] wlan0: associate with <MAC address removed> (try 1)
[  169.576048] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  169.576057] wlan0: associated
[  173.541697] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  176.028244] wlan0: authenticate with <MAC address removed> (try 1)
[  176.032409] wlan0: authenticated
[  176.032582] wlan0: associate with <MAC address removed> (try 1)
[  176.035529] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  176.035533] wlan0: associated
[  179.073832] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  183.122577] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  188.702726] wlan0: authenticate with <MAC address removed> (try 1)
[  188.704649] wlan0: authenticated
[  188.704933] wlan0: associate with <MAC address removed> (try 1)
[  188.707556] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  188.707564] wlan0: associated
[  188.713464] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  192.671341] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  195.148553] wlan0: authenticate with <MAC address removed> (try 1)
[  195.150428] wlan0: authenticated
[  195.151948] wlan0: associate with <MAC address removed> (try 1)
[  195.154315] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  195.154319] wlan0: associated
[  199.121422] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  201.618675] wlan0: authenticate with <MAC address removed> (try 1)
[  201.620534] wlan0: authenticated
[  201.620661] wlan0: associate with <MAC address removed> (try 1)
[  201.623079] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  201.623083] wlan0: associated
[  205.590989] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  208.070515] wlan0: authenticate with <MAC address removed> (try 1)
[  208.072467] wlan0: authenticated
[  208.077922] wlan0: associate with <MAC address removed> (try 1)
[  208.080317] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  208.080320] wlan0: associated
[  212.050898] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  214.544057] wlan0: authenticate with <MAC address removed> (try 1)
[  214.549568] wlan0: authenticated
[  214.549725] wlan0: associate with <MAC address removed> (try 1)
[  214.552159] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  214.552163] wlan0: associated
[  218.520692] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  220.999186] wlan0: authenticate with <MAC address removed> (try 1)
[  221.001040] wlan0: authenticated
[  221.001713] wlan0: associate with <MAC address removed> (try 1)
[  221.007328] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  221.007337] wlan0: associated
[  224.970567] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  227.456100] wlan0: authenticate with <MAC address removed> (try 1)
[  227.458020] wlan0: authenticated
[  227.458670] wlan0: associate with <MAC address removed> (try 1)
[  227.461145] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  227.461148] wlan0: associated
[  231.430423] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  233.901261] wlan0: authenticate with <MAC address removed> (try 1)
[  233.903186] wlan0: authenticated
[  233.907780] wlan0: associate with <MAC address removed> (try 1)
[  233.910239] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  233.910248] wlan0: associated
[  237.870264] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  240.366682] wlan0: authenticate with <MAC address removed> (try 1)
[  240.368600] wlan0: authenticated
[  240.369861] wlan0: associate with <MAC address removed> (try 1)
[  240.375541] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  240.375545] wlan0: associated
[  244.346366] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  246.812996] wlan0: authenticate with <MAC address removed> (try 1)
[  246.815983] wlan0: authenticated
[  246.817953] wlan0: associate with <MAC address removed> (try 1)
[  246.820338] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  246.820341] wlan0: associated
[  247.008692] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  254.901142] wlan0: authenticate with <MAC address removed> (try 1)
[  254.903070] wlan0: authenticated
[  254.903286] wlan0: associate with <MAC address removed> (try 1)
[  254.905672] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  254.905676] wlan0: associated
[  258.869773] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  261.344577] wlan0: authenticate with <MAC address removed> (try 1)
[  261.346425] wlan0: authenticated
[  261.346862] wlan0: associate with <MAC address removed> (try 1)
[  261.349335] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  261.349344] wlan0: associated
[  265.309654] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  267.804118] wlan0: authenticate with <MAC address removed> (try 1)
[  267.805950] wlan0: authenticated
[  267.806386] wlan0: associate with <MAC address removed> (try 1)
[  267.820398] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  267.820408] wlan0: associated
[  271.799504] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  274.267324] wlan0: authenticate with <MAC address removed> (try 1)
[  274.270214] wlan0: authenticated
[  274.272594] wlan0: associate with <MAC address removed> (try 1)
[  274.274958] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  274.274966] wlan0: associated
[  278.240508] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  280.707388] wlan0: authenticate with <MAC address removed> (try 1)
[  280.709204] wlan0: authenticated
[  280.710082] wlan0: associate with <MAC address removed> (try 1)
[  280.716485] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  280.716494] wlan0: associated
[  284.682876] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  287.162832] wlan0: authenticate with <MAC address removed> (try 1)
[  287.167615] wlan0: authenticated
[  287.170724] wlan0: associate with <MAC address removed> (try 1)
[  287.173195] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  287.173204] wlan0: associated
[  291.141577] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  293.623248] wlan0: authenticate with <MAC address removed> (try 1)
[  293.625063] wlan0: authenticated
[  293.625328] wlan0: associate with <MAC address removed> (try 1)
[  293.627785] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  293.627794] wlan0: associated
[  297.598909] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  300.090871] wlan0: authenticate with <MAC address removed> (try 1)
[  300.092752] wlan0: authenticated
[  300.093043] wlan0: associate with <MAC address removed> (try 1)
[  300.095435] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  300.095443] wlan0: associated
[  304.058780] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  306.532824] wlan0: authenticate with <MAC address removed> (try 1)
[  306.534671] wlan0: authenticated
[  306.538072] wlan0: associate with <MAC address removed> (try 1)
[  306.540532] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  306.540541] wlan0: associated
[  310.508778] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  312.992927] wlan0: authenticate with <MAC address removed> (try 1)
[  312.994781] wlan0: authenticated
[  312.997225] wlan0: associate with <MAC address removed> (try 1)
[  312.999604] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  312.999613] wlan0: associated
[  313.006090] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  313.024366] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  318.888944] wlan0: authenticate with <MAC address removed> (try 1)
[  318.890766] wlan0: authenticated
[  318.891326] wlan0: associate with <MAC address removed> (try 1)
[  318.893693] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  318.893697] wlan0: associated
[  322.858275] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  325.323901] wlan0: authenticate with <MAC address removed> (try 1)
[  325.325872] wlan0: authenticated
[  325.326333] wlan0: associate with <MAC address removed> (try 1)
[  325.328697] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  325.328705] wlan0: associated
[  329.298147] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  331.780304] wlan0: authenticate with <MAC address removed> (try 1)
[  331.786433] wlan0: authenticated
[  331.788668] wlan0: associate with <MAC address removed> (try 1)
[  331.797450] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  331.797454] wlan0: associated
[  335.758017] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  338.233440] wlan0: authenticate with <MAC address removed> (try 1)
[  338.238678] wlan0: authenticated
[  338.239698] wlan0: associate with <MAC address removed> (try 1)
[  338.244462] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  338.244471] wlan0: associated
[  342.208516] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  344.687011] wlan0: authenticate with <MAC address removed> (try 1)
[  344.689861] wlan0: authenticated
[  344.690622] wlan0: associate with <MAC address removed> (try 1)
[  344.695949] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  344.695958] wlan0: associated
[  348.659713] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  351.147914] wlan0: authenticate with <MAC address removed> (try 1)
[  351.151587] wlan0: authenticated
[  351.152227] wlan0: associate with <MAC address removed> (try 1)
[  351.154593] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  351.154601] wlan0: associated
[  355.117706] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  357.604510] wlan0: authenticate with <MAC address removed> (try 1)
[  357.606463] wlan0: authenticated
[  357.606767] wlan0: associate with <MAC address removed> (try 1)
[  357.609154] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  357.609162] wlan0: associated
[  361.577403] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  364.048534] wlan0: authenticate with <MAC address removed> (try 1)
[  364.051238] wlan0: authenticated
[  364.053642] wlan0: associate with <MAC address removed> (try 1)
[  364.056076] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  364.056080] wlan0: associated
[  368.017479] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  370.491250] wlan0: authenticate with <MAC address removed> (try 1)
[  370.497942] wlan0: authenticated
[  370.498260] wlan0: associate with <MAC address removed> (try 1)
[  370.502818] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  370.502822] wlan0: associated
[  374.467140] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  376.968084] wlan0: authenticate with <MAC address removed> (try 1)
[  376.970004] wlan0: authenticated
[  376.971923] wlan0: associate with <MAC address removed> (try 1)
[  376.980855] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  376.980859] wlan0: associated
[  377.003440] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  399.031082] wlan0: authenticate with <MAC address removed> (try 1)
[  399.036064] wlan0: authenticated
[  399.038578] wlan0: associate with <MAC address removed> (try 1)
[  399.041451] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  399.041455] wlan0: associated
[  403.006445] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  405.480967] wlan0: authenticate with <MAC address removed> (try 1)
[  405.483124] wlan0: authenticated
[  405.483312] wlan0: associate with <MAC address removed> (try 1)
[  405.485746] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  405.485750] wlan0: associated
[  409.447881] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  411.941943] wlan0: authenticate with <MAC address removed> (try 1)
[  411.943752] wlan0: authenticated
[  411.944216] wlan0: associate with <MAC address removed> (try 1)
[  411.946551] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  411.946554] wlan0: associated
[  412.375086] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  462.016069] wlan0: authenticate with <MAC address removed> (try 1)
[  462.023648] wlan0: authenticated
[  462.026337] wlan0: associate with <MAC address removed> (try 1)
[  462.028769] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  462.028773] wlan0: associated
[  465.994976] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  468.463562] wlan0: authenticate with <MAC address removed> (try 1)
[  468.467253] wlan0: authenticated
[  468.471086] wlan0: associate with <MAC address removed> (try 1)
[  468.474813] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  468.474817] wlan0: associated
[  472.434872] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  474.921007] wlan0: authenticate with <MAC address removed> (try 1)
[  474.923250] wlan0: authenticated
[  474.924070] wlan0: associate with <MAC address removed> (try 1)
[  474.926454] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  474.926463] wlan0: associated
[  478.904995] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  481.378524] wlan0: authenticate with <MAC address removed> (try 1)
[  481.380503] wlan0: authenticated
[  481.380938] wlan0: associate with <MAC address removed> (try 1)
[  481.383323] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  481.383332] wlan0: associated
[  485.344579] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  487.819397] wlan0: authenticate with <MAC address removed> (try 1)
[  487.821385] wlan0: authenticated
[  487.822886] wlan0: associate with <MAC address removed> (try 1)
[  487.825263] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  487.825266] wlan0: associated
[  491.794655] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  494.266672] wlan0: authenticate with <MAC address removed> (try 1)
[  494.272035] wlan0: authenticated
[  494.272262] wlan0: associate with <MAC address removed> (try 1)
[  494.274597] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  494.274602] wlan0: associated
[  498.244283] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  500.714390] wlan0: authenticate with <MAC address removed> (try 1)
[  500.722731] wlan0: authenticated
[  500.722906] wlan0: associate with <MAC address removed> (try 1)
[  500.725317] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  500.725322] wlan0: associated
[  504.694196] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  507.155641] wlan0: authenticate with <MAC address removed> (try 1)
[  507.157550] wlan0: authenticated
[  507.158126] wlan0: associate with <MAC address removed> (try 1)
[  507.165033] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  507.165043] wlan0: associated
[  511.134058] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  513.600452] wlan0: authenticate with <MAC address removed> (try 1)
[  513.602500] wlan0: authenticated
[  513.605771] wlan0: associate with <MAC address removed> (try 1)
[  513.608222] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  513.608231] wlan0: associated
[  517.573829] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  925.448653] wlan0: authenticate with <MAC address removed> (try 1)
[  925.450525] wlan0: authenticated
[  925.453871] wlan0: associate with <MAC address removed> (try 1)
[  925.457397] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  925.457401] wlan0: associated
[  929.426905] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  931.903875] wlan0: authenticate with <MAC address removed> (try 1)
[  931.906405] wlan0: authenticated
[  931.907205] wlan0: associate with <MAC address removed> (try 1)
[  931.913211] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  931.913221] wlan0: associated
[  935.876799] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  938.343063] wlan0: authenticate with <MAC address removed> (try 1)
[  938.345002] wlan0: authenticated
[  938.345566] wlan0: associate with <MAC address removed> (try 1)
[  938.351092] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  938.351101] wlan0: associated
[  942.316589] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  944.784860] wlan0: authenticate with <MAC address removed> (try 1)
[  944.789808] wlan0: authenticated
[  944.789988] wlan0: associate with <MAC address removed> (try 1)
[  944.793403] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  944.793407] wlan0: associated
[  948.127964] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  950.785574] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  956.332757] wlan0: authenticate with <MAC address removed> (try 1)
[  956.336258] wlan0: authenticated
[  956.336510] wlan0: associate with <MAC address removed> (try 1)
[  956.338808] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  956.338817] wlan0: associated
[  956.342318] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  960.306730] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  962.779209] wlan0: authenticate with <MAC address removed> (try 1)
[  962.783159] wlan0: authenticated
[  962.783567] wlan0: associate with <MAC address removed> (try 1)
[  962.785981] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  962.785989] wlan0: associated
[  966.756066] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  969.241179] wlan0: authenticate with <MAC address removed> (try 1)
[  969.243138] wlan0: authenticated
[  969.249455] wlan0: associate with <MAC address removed> (try 1)
[  969.253035] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  969.253038] wlan0: associated
[  973.215948] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  975.688524] wlan0: authenticate with <MAC address removed> (try 1)
[  975.691879] wlan0: authenticated
[  975.692501] wlan0: associate with <MAC address removed> (try 1)
[  975.694941] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  975.694951] wlan0: associated
[  979.655744] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  982.120180] wlan0: authenticate with <MAC address removed> (try 1)
[  982.123728] wlan0: authenticated
[  982.126797] wlan0: associate with <MAC address removed> (try 1)
[  982.130235] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  982.130245] wlan0: associated
[  986.095592] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  988.558388] wlan0: authenticate with <MAC address removed> (try 1)
[  988.561067] wlan0: authenticated
[  988.561643] wlan0: associate with <MAC address removed> (try 1)
[  988.564100] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  988.564109] wlan0: associated
[  989.369478] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

****************** done ******************




```

---

### Post by courseinmiracles2 on 2013-10-21
I am pretty much in the same sort of boat and have a thread
[h=3][13.10 wireless won't connect to specific router]("http://ubuntuforums.org/showthread.php?t=2182286")[/h]
It's not quite the same problem but you may want to keep an eye on it. The post below tells you how to run a wireless script that will give details of your network. run it and post the details, it may be helpful for someone trying to help you.
[http://ubuntuforums.org/showthread.php?t=2176886&highlight=13.10+won%27t+connect+wireless+network](http://ubuntuforums.org/showthread.php?t=2176886&highlight=13.10+won%27t+connect+wireless+network)

Good Luck

---

### Post by GammaPoint on 2013-10-21
Thanks courseinmiracles2, I just added the output of the script to my first post.

---

### Post by vivekkholia on 2013-10-22
I have the same problem with my **toshiba satellite L640** laptop... I've read many threads similar to this topic. I tried different solutions but nothing is working.
Today I tried a different approach. **I booted up** **in recovery mode and the wifi was working properly**. Not sure what's going on here. Probably some network related settings are messd up I suppose.
Here is the output of the wireless script:
```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.2.0-54-generic-pae #82-Ubuntu SMP Tue Sep 10 20:29:22 UTC 2013 i686 athlon i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7175]
    Kernel driver in use: wl
--
08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Kernel driver in use: atl1c

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 005 Device 002: ID 0930:0214 Toshiba Corp. 

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

wl                   2906597  0 
cfg80211              178877  1 wl
lib80211               14040  2 lib80211_crypt_tkip,wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
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
    Address:         192.168.1.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    iBall-Baton:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    NETGEAR06:       Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 100 WPA2



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

no-auto-default=<MAC address removed>,AA:00:04:00:0A:04,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
#provider dsl-provider

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-11 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR06"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00094E4554474541523036
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A0001101044000102103B000103104700106304125310192006122800000000004C1021000D4E65746765617220436F72702E1023000A4E6574676561722041501024000D45562D323031322D30382D30341042000F3132333435363738393031323334371054000800060050F2040001101100134E65746765617220576972656C657373204150100800020086
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 3996ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD180050F2020101830003A7000027A9000042455E0062332F00
                    IE: Unknown: DD080013920100018500
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 3996ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: DD180050F2020101830003A7000027A9000042455E0062332F00
                    IE: Unknown: DD080013920100018500
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"iBall-Baton"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000B6942616C6C2D4261746F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060D0000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0E0050F204104A0001101044000102


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

filename:       /lib/modules/3.2.0-54-generic-pae/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:06.0/0000:08:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[    9.219425] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.219476] wl 0000:02:00.0: setting latency timer to 64
[    9.251764] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    9.478232] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[    9.966842] ADDRCONF(NETDEV_UP): eth1: link is not ready

****************** done ******************

```

---

### Post by GammaPoint on 2013-10-22
I just wanted to report that the wireless started working again last night. I can't exactly say what fixed it, since I was rebooting often (and since it broke unexpectedly, there's no reason really to suspect that this apparent randomness won't fix itself as well). However, one of the things I did right before it started working again was to delete my Wifi network in the network manager. It automatically detected it again and added it back in. After a reboot it automagically worked.

---

### Post by vivekkholia on 2013-10-22
> However, one of the things I did right before it started working again  was to delete my Wifi network in the network manager. It automatically  detected it again and added it back in. After a reboot it automagically  worked.                 

Thanks man! It worked for me too.:)

EDIT: The problem occured again after few restarts. However I was able to solve it. I have a broadcom BCM4313 wireless card. I read in some recent posts that the updated drivers for these BCM43xx series cards have some serious problems. I rememberd that I installed the proprietary driver for wifi card from System Settings > Additional Drivers. So I removed the proprietary driver. After that I rebooted the laptop and I was able to use wifi.

---

