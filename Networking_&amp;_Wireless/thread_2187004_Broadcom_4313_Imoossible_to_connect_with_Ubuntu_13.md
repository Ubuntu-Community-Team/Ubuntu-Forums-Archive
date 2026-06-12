---
title: "Broadcom 4313 Imoossible to connect with Ubuntu 13.04 using wireless"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by F00RAX on 2013-11-10
Hello! Since I use Ubuntu 13.04, I'm unable to connect to a crypted wireless network. If I connect to my home network (SSID : "TheSwissGuy") it will keep trying to connect for about 5 min. and then it ask me again for the password...
I think it work if I connect to a "WEP" wireless network but mine is a "WPA WPA2"
 I runed this script for more informations :[URL="http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385"]

http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385[/URL]

And here is the results :

```


*************** info trace ***************


***** uname -a *****


Linux cyril-HP-Folio-13-Notebook-PC 3.8.0-33-generic #48-Ubuntu SMP Wed Oct 23 09:16:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:17f8]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 005: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c07 Sunplus Innovation Technology Inc. 
Bus 001 Device 004: ID 0a5c:21e3 Broadcom Corp. 


***** PCMCIA Card Info *****




***** iwconfig *****


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


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


wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              511019  1 wl


***** nm-tool *****


NetworkManager Tool


State: connected (global)


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
    'murca:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    This-Is-NOT-Skynet_I'llbeback: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 67 WPA
    EMTS:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    OnNetworks54:    Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 45 WPA2
    PornHub:         Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    HU:              Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Markovnikov:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Disco'n'stuff:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Coco:            Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA2
    NETGEAR-Guest:   Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 29 WPA
    Golvmopp:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Esgusodwch fi!:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Knox o Sofia:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Veronica:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Soffan:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA
    ANJJ:            Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 15 WPA
    ForzaBajen:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    CsMbP:           Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 44 WEP
    WiFi:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WEP
    dlink:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    TheSwissGuy:     Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    TP-LINK_905B60:  Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Mangazdalen:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Wintermute:      Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    One does not simply steal a WiFi: Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 14 WPA2
    06_i.Gokcek:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WEP
    Wifivic:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    OnNetworks97:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA2
    NETGEAR80:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA2
    M+A:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2
    Inferno:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    dlink:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WEP
    Ankh-Morpork:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Therese2:        Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Tdlink:          Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 12 WEP
    dlinktmm:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    YoMama:          Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2




- Device: eth0  [Ethernet automatique] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1




- VPN:  [EPFL - VPN] -----------------------------------------------------------
  State:             connected
  Default:           yes


  Message:






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


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00024855
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 02 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"TheSwissGuy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000B5468655377697373477579
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1013FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1608000500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020039127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD8C0050F204104A00011010440001021057000101103B00010310470010BC329E001DD811B28601C8BE195EEB9810210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400084449522D3633364C1042000830303030303030301054000800060050F2040001101100084449522D3633364C10080002208C103C0001011049000600372A000120
          Cell 03 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"OnNetworks54"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000C4F6E4E6574776F726B733534
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050401020002
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A0C111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080800000000000000000000000000000000000000
                    IE: Unknown: 3D1605080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"'murca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0006276D75726361
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"EMTS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0004454D5453
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880FC751678F7B5103C000101
                    IE: Unknown: 050400010004
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
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
                    IE: Unknown: 0B0501008B127A
                    IE: Unknown: DD07000C4307000000
          Cell 06 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"This-Is-NOT-Skynet_I'llbeback"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 001D546869732D49732D4E4F542D536B796E65745F49276C6C62656261636B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 07 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"PornHub"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0007506F726E487562
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030108
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16080F1600000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34080F1600000000000000000000000000000000000000
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Knox o Sofia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000C4B6E6F78206F20536F666961
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
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"CsMbP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000543734D6250
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080000000000000000000000000000000000000000
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Disco'n'stuff"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000D446973636F276E277374756666
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
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A400004243BC0062326600
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081100000000000000000000000000000000000000
          Cell 11 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Coco"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0004436F636F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608001300000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408001300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 12 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000D4E4554474541522D4775657374
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0600E04C020160
          Cell 13 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"06_i.Gokcek"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000B30365F692E476F6B63656B
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 14 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Soffan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0006536F6666616E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400030008
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 15 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Mangazdalen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000B4D616E67617A64616C656E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001900000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010004000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 16 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_905B60"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000E54502D4C494E4B5F393035423630
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1608071100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001
          Cell 17 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Veronica"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00085665726F6E696361
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880CCB255F58952103C000101
                    IE: Unknown: 050400010006
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000000000000000000000000000000000000000000
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
                    IE: Unknown: 0B05000087127A
                    IE: Unknown: DD07000C4307000000




***** resolv.conf *****


nameserver 127.0.0.1
search epfl.ch


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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist hp_wmi


[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist bcma
blacklist brcmsmac
blacklist ssb


***** modinfo *****


filename:       /lib/modules/3.8.0-33-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-33-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[    3.497367] wl: module license 'MIXED/Proprietary' taints kernel.
[    3.512513] Bluetooth: can't load firmware, may not work correctly
[    3.541215] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    3.798733] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[    8.782365] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4724.950890] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 4775.771527] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 4824.280027] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 4874.387198] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 5220.961305] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 5274.127542] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 5325.559441] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 5377.738510] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 5476.449201] ERROR @wl_dev_intvar_get : error (-1)
[ 5476.449208] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 5542.540081] ERROR @wl_dev_intvar_get : error (-1)
[ 5542.540092] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 6168.544750] IPv6: eth1: IPv6 duplicate address fe80::6627:37ff:fe57:b0f4 detected!
[ 6243.629277] ERROR @wl_dev_intvar_get : error (-1)
[ 6243.629282] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 6358.112732] ERROR @wl_dev_intvar_get : error (-1)
[ 6358.112736] ERROR @wl_cfg80211_get_tx_power : error (-1)


****************** done ******************



```

Thanks for helping! 

Regards

---

### Post by praseodym on 2013-11-10
Try a fixed channel with 20MHz bandwidth instead of 20/40MHz. Change to pure WPA2-AES if possible

---

### Post by F00RAX on 2013-11-10
I cannot change this on my router because the install-CD is for windows users only... 
And I don't think I could change it if any.
Thank you

---

### Post by praseodym on 2013-11-10
You dont need a CD. Connect via cable and type the IP address of the router into your browsers URL-line. Login and password should be sticked on you router with a label. Check the router manual.

---

### Post by chili555 on 2013-11-10
Please check here:  [http://askubuntu.com/questions/359262/difficulties-with-bcm4313-driver-in-ubuntu-studio-13-04/359406#359406](http://askubuntu.com/questions/359262/difficulties-with-bcm4313-driver-in-ubuntu-studio-13-04/359406#359406)> In Ubuntu 13.04, I believe the default bcmwl-kernel-source will not work correctly for your Broadcom 4313. ...etc.

---

### Post by F00RAX on 2013-11-13
Thanks a lot [[COLOR=#000000]chili555[/COLOR]]("http://ubuntuforums.org/member.php?u=35909")[COLOR=#000000] [/COLOR] it worked!

---

### Post by chili555 on 2013-11-13
> **F00RAX said:**
> Thanks a lot [[COLOR=#000000]chili555[/COLOR]]("http://ubuntuforums.org/member.php?u=35909")[COLOR=#000000] [/COLOR] it worked!
Awesome! Glad it's working.

---

### Post by docarchy on 2013-11-26
> **chili555 said:**
> Please check here:  [http://askubuntu.com/questions/359262/difficulties-with-bcm4313-driver-in-ubuntu-studio-13-04/359406#359406](http://askubuntu.com/questions/359262/difficulties-with-bcm4313-driver-in-ubuntu-studio-13-04/359406#359406)Chili555, had the same exact problem as the OP and your solution fixed this for me as well. Thank you.

---

### Post by F00RAX on 2014-05-30
Solved on Ubuntu 14.04 LTS

---

