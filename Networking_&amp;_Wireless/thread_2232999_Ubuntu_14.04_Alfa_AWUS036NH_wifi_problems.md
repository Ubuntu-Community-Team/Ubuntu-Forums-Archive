---
title: "Ubuntu 14.04 Alfa AWUS036NH wifi problems"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by raymondabrown14 on 2014-07-05
I know there have been similar post on this subject but none have fixed my problem.

Before I updated Ubuntu to 14.04 my Alfa Usb card worked fine but after the update it has a problem connecting to one specific network.  I can connect to another network sometimes without problems but most of the time I have to keep unplugging and plugging back in my card.  When I use the card in VM workstation on both windows 7 and Kali-linux it works just fine but with Ubuntu it won't connect.

I ran the script recommended by varunendra and here's the first 10 pages... It's to long to post the entire thing.

```
########## wireless info START ##########

##### release #####

Distributor ID:    UbuntuDescription:    Ubuntu 14.04 LTSRelease:    14.04Codename:    trusty

##### kernel #####

Linux berks 3.13.0-30-generic #54-Ubuntu SMP Mon
Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

00:19.0 Ethernet controller [0200]: Intel
Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)    Subsystem: Dell Device [1028:0233]    Kernel driver in use: e1000e

0c:00.0 Network controller [0280]: Broadcom
Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)    Subsystem: Dell Wireless 1397 WLAN Mini-Card
[1028:000c]    Kernel driver in use: b43-pci-bridge

##### lsusb #####

Bus 002 Device 013: ID 148f:3070 Ralink
Technology, Corp. RT2870/RT3070 Wireless AdapterBus 002 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hubBus 008 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hubBus 007 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hubBus 006 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hubBus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hubBus 005 Device 002: ID 0a5c:5800 Broadcom Corp.
BCM5880 Secure Applications ProcessorBus 005 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hubBus 004 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hubBus 003 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: dell-wifi: Wireless LAN    Soft blocked: no    Hard blocked: no1: phy0: Wireless LAN    Soft blocked: no    Hard blocked: no16: phy15: Wireless LAN    Soft blocked: no    Hard blocked: no

##### lsmod #####

iwlwifi               169932  0 
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usbrt2800lib              89076  1 rt2800usbrt2x00lib              55307  3
rt2x00usb,rt2800lib,rt2800usbcrc_ccitt              12707  1 rt2800libb43                   387371  0 
bcma                   52096  1 b43mac80211              626557  4
b43,rt2x00lib,rt2x00usb,rt2800libcfg80211              484040  4
b43,iwlwifi,mac80211,rt2x00libssb                    62379  1 b43

##### iw reg get #####

country US:    (2402 - 2472 @ 40), (3, 27)    (5170 - 5250 @ 40), (3, 17)    (5250 - 5330 @ 40), (3, 20), DFS    (5490 - 5600 @ 40), (3, 20), DFS    (5650 - 5710 @ 40), (3, 20), DFS    (5735 - 5835 @ 40), (3, 30)    (57240 - 63720 @ 2160), (N/A, 40)

##### interfaces #####

# interfaces(5) file used by ifup(8) and
ifdown(8)auto loiface lo inet loopback

up iwconfig wlan0 rate 36M

##### iwconfig #####

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point:
Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off  
Fragment thr:off          Power Management:off          
wlan0     IEEE 802.11bgn  ESSID:"50IC4"
 
          Mode:Managed  Frequency:2.412 GHz 
Access Point: <MAC address removed>   
          Bit Rate=24 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off  
Fragment thr:off          Power Management:on          Link Quality=41/70  Signal level=-69
dBm  
          Rx invalid nwid:0  Rx invalid crypt:0 
Rx invalid frag:0          Tx excessive retries:1  Invalid
misc:73   Missed beacon:0

##### route #####

Kernel IP routing tableDestination     Gateway         Genmask        
Flags Metric Ref    Use Iface0.0.0.0         192.168.1.1     0.0.0.0        
UG    0      0        0 wlan0192.168.1.0     0.0.0.0         255.255.255.0  
U     9      0        0 wlan0192.168.67.0    0.0.0.0         255.255.255.0  
U     0      0        0 vmnet1192.168.215.0   0.0.0.0         255.255.255.0  
U     0      0        0 vmnet8

##### resolv.conf #####

nameserver 127.0.1.1search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Auto 50IC4]
--------------------------------------------------  Type:              802.11 WiFi  Driver:            rt2800usb  State:             connected  Default:           yes  HW Address:        <MAC address removed>

  Capabilities:    Speed:           18 Mb/s

  Wireless Properties    WEP Encryption:  yes    WPA Encryption:  yes    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)    95VC8:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA2    belkin.712:      Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2    CBCI-AC77-2.4:   Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2    verizon:         Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP    J6OE4:           Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP    C98B2:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP    84RV6:           Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WEP    *50IC4:          Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WEP    HOME-7D22:       Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2    ngHub_31943CNP033CD: Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2    NWDW6:           Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WEP    0UTT5:           Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WEP    WA5M5:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP    xfinitywifi:     Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72    xfinitywifi:     Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45    Tamzin4:         Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2    HSQ64:           Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WEP    9P9B3:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2    HOME-EFF4:       Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2    vi-02fC02fc:     Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2

  IPv4 Settings:    Address:         192.168.1.9    Prefix:          24 (255.255.255.0)    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan1
----------------------------------------------------------------  Type:              802.11 WiFi  Driver:            b43  State:             disconnected  Default:           no  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties    WEP Encryption:  yes    WPA Encryption:  yes    WPA2 Encryption: yes

  Wireless Access Points 
    CBCI-AC77-2.4:   Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2    95VC8:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2    belkin.712:      Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2    0UTT5:           Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WEP    verizon:         Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WEP    50IC4:           Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WEP    WA5M5:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WEP    C98B2:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP    DFD40:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP    ngHub_31943CNP033CD: Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2    HOME-7D22:       Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2    HOME-9B89-2.4:   Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2    HOME-86EB:       Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2    J6OE4:           Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP    V7I31:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WEP    vi-02fC02fc:     Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2    84RV6:           Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WEP    DHM:             Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2    ddlldrinc:       Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WEP    HOME-F4C2:       Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2    NWDW6:           Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WEP    xfinitywifi:     Infra, <MAC address
removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35    xfinitywifi:     Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67    YTQ83:           Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2    W88D0:           Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP    xfinitywifi:     Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17

- Device: eth0
-----------------------------------------------------------------  Type:              Wired  Driver:            e1000e  State:             unavailable  Default:           no  HW Address:        <MAC address removed>

  Capabilities:    Carrier Detect:  yes

  Wired Properties    Carrier:         off

##### NetworkManager.state #####

[main]NetworkingEnabled=trueWirelessEnabled=trueWWANEnabled=trueWimaxEnabled=true

##### NetworkManager.conf #####

[main]plugins=ifupdown,keyfile,ofonodns=dnsmasq

no-auto-default=

[ifupdown]managed=false

##### iwlist #####

wlan1     Scan completed :          Cell 01 - Address: <MAC address
removed>                    Channel:11                    Frequency:2.462 GHz (Channel
11)                    Quality=54/70  Signal
level=-56 dBm  
                    Encryption key:off                    ESSID:"xfinitywifi"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 6 Mb/s                              9 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=000000895690d035                    Extra: Last beacon: 32ms ago                    IE: Unknown:
000B7866696E69747977696669                    IE: Unknown:
010882848B960C121824                    IE: Unknown: 03010B                    IE: Unknown:
0706555320010B1E                    IE: Unknown: 2A0100                    IE: Unknown: 32043048606C                    IE: Unknown:
2D1AAD011BFFFFFF00000000000000000080000000000406E6E70D00                    IE: Unknown:
331AAD011BFFFFFF00000000000000000080000000000406E6E70D00                    IE: Unknown:
3D160B000500000000000000000000000000000000000000                    IE: Unknown:
34160B000500000000000000000000000000000000000000                    IE: Unknown:
4A0E14000A002C01C800140005001900                    IE: Unknown: 7F050100000000                    IE: Unknown:
DD180050F2020101880003A4000027A4000042435E0062322F00                    IE: Unknown:
DD0900037F01010000FF7F          Cell 02 - Address: <MAC address
removed>                    Channel:1                    Frequency:2.412 GHz (Channel
1)                    Quality=25/70  Signal
level=-85 dBm  
                    Encryption key:on                    ESSID:""                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 9 Mb/s                              18 Mb/s; 36 Mb/s;
54 Mb/s                    Bit Rates:6 Mb/s; 12 Mb/s;
24 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=0000008958b18ca9                    Extra: Last beacon: 26760ms
ago                    IE: Unknown: 0000                    IE: Unknown:
010882848B961224486C                    IE: Unknown: 030101                    IE: Unknown: 32048C98B060                    IE: Unknown:
0706555320010B14                    IE: Unknown: 050400010000                    IE: Unknown: 2A0104                    IE: Unknown:
2D1A8E1117FFFF000001000000000000000000000000000000000000                    IE: Unknown:
3D1601000500000000000000000000000000000000000000                    IE: Unknown:
4A0E14000A002C01C800140005001900                    IE: Unknown: 7F0101                    IE: IEEE 802.11i/WPA2
Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) :
CCMP                        Authentication Suites
(1) : PSK                    IE: Unknown:
DD180050F2020101000003A4000027A4000042435E0062322F00                    IE: Unknown: 0B05010092127A                    IE: Unknown:
DD07000C4303000000          Cell 03 - Address: <MAC address
removed>                    Channel:1                    Frequency:2.412 GHz (Channel
1)                    Quality=47/70  Signal
level=-63 dBm  
                    Encryption key:on                    ESSID:"belkin.712"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s;
54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12
Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=00000056e8bf6b9e                    Extra: Last beacon: 780ms
ago                    IE: Unknown:
000A62656C6B696E2E373132                    IE: Unknown:
010882840B162430486C                    IE: Unknown: 030101                    IE: Unknown: 2A0104                    IE: Unknown: 2F0104                    IE: IEEE 802.11i/WPA2
Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) :
CCMP                        Authentication Suites
(1) : PSK                    IE: Unknown: 32040C121860                    IE: Unknown:
2D1AFC181BFFFF000000000000000000000000000000000000000000                    IE: Unknown:
3D1601080400000000000000000000000000000000000000                    IE: Unknown:
4A0E14000A002C01C800140005001900                    IE: Unknown: 7F0101                    IE: Unknown:
DDA20050F204104A00011010440001021041000100103B00010310470010C342311D70AB2C94A63581233745E10C1021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303220763110240007312E30302E30391042000E31323131333147463130363033391054000800060050F20400011011001D42656C6B696E204E363030444220576972656C65737320526F75746572100800020084                    IE: Unknown:
DD090010180204F0040000                    IE: WPA Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) :
CCMP                        Authentication Suites
(1) : PSK                    IE: Unknown:
DD180050F2020101800003A4000027A4000042435E0062322F00          Cell 04 - Address: <MAC address
removed>                    Channel:1                    Frequency:2.412 GHz (Channel
1)                    Quality=52/70  Signal
level=-58 dBm  
                    Encryption key:on                    ESSID:"NWDW6"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 6 Mb/s; 9 Mb/s                              11 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=00000009837c7c15                    Extra: Last beacon: 32ms ago                    IE: Unknown: 00054E57445736                    IE: Unknown:
010882848B0C12961824                    IE: Unknown: 030101                    IE: Unknown:
0706555320010B1B                    IE: Unknown: 200100                    IE: Unknown: 2A0100                    IE: Unknown: 32043048606C                    IE: Unknown:
DD180050F2020101830003A4000027A4000042435E0062322F00          Cell 05 - Address: <MAC address
removed>                    Channel:6                    Frequency:2.437 GHz (Channel
6)                    Quality=60/70  Signal
level=-50 dBm  
                    Encryption key:on                    ESSID:"95VC8"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 6 Mb/s                              9 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=00000089585f437a                    Extra: Last beacon: 32ms ago                    IE: Unknown: 00053935564338                    IE: Unknown:
010882848B960C121824                    IE: Unknown: 030106                    IE: Unknown: 200100                    IE: IEEE 802.11i/WPA2
Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) :
CCMP                        Authentication Suites
(1) : PSK                    IE: Unknown: 2A0100                    IE: Unknown: 32043048606C                    IE: Unknown:
DD180050F2020101040003A4000027A4000042435E0062322F00                    IE: Unknown:
2D1A8C131BFFFF000000000000000000000000000000000000000000                    IE: Unknown:
3D1606080800000000000000000000000000000000000000                    IE: Unknown:
DD0900037F01010000FF7F                    IE: Unknown:
DD0A00037F04010000000000                    IE: Unknown:
0706555320010B1B          Cell 06 - Address: <MAC address
removed>                    Channel:6                    Frequency:2.437 GHz (Channel
6)                    Quality=28/70  Signal
level=-82 dBm  
                    Encryption key:on                    ESSID:"DFD40"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 6 Mb/s                              9 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=000000895cc6d249                    Extra: Last beacon: 296ms
ago                    IE: Unknown: 00054446443430                    IE: Unknown:
010882848B960C121824                    IE: Unknown: 030106                    IE: Unknown: 050400010000                    IE: Unknown:
0706555320010B1B                    IE: Unknown: 200100                    IE: Unknown: 2A0102                    IE: Unknown: 32043048606C                    IE: Unknown:
DD180050F2020101830003A4000027A4000042435E0062322F00                    IE: Unknown:
DD0900037F010100200000          Cell 07 - Address: <MAC address
removed>                    Channel:6                    Frequency:2.437 GHz (Channel
6)                    Quality=23/70  Signal
level=-87 dBm  
                    Encryption key:on                    ESSID:"V7I31"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 6 Mb/s                              9 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=000000895a852199                    Extra: Last beacon: 23308ms
ago                    IE: Unknown: 00055637493331                    IE: Unknown:
010882848B960C121824                    IE: Unknown: 030106                    IE: Unknown: 200100                    IE: Unknown: 2A0100                    IE: Unknown: 32043048606C                    IE: Unknown:
DD180050F2020101030003A4000027A4000042435E0062322F00                    IE: Unknown:
2D1A8C131BFF00000000000000000000000000000000000000000000                    IE: Unknown:
3D1606001B00000000000000000000000000000000000000                    IE: Unknown:
DD0900037F01010000FF7F                    IE: Unknown:
DD0A00037F04010020000000                    IE: Unknown:
0706555320010B1B          Cell 08 - Address: <MAC address
removed>                    Channel:6                    Frequency:2.437 GHz (Channel
6)                    Quality=30/70  Signal
level=-80 dBm  
                    Encryption key:on                    ESSID:"WA5M5"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 6 Mb/s                              9 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=000000895c436527                    Extra: Last beacon: 796ms
ago                    IE: Unknown: 00055741354D35                    IE: Unknown:
010882848B960C121824                    IE: Unknown: 030106                    IE: Unknown: 200100                    IE: Unknown: 2A0100                    IE: Unknown: 32043048606C                    IE: Unknown:
DD180050F2020101030003A4000027A4000042435E0062322F00                    IE: Unknown:
2D1A8C131BFF00000000000000000000000000000000000000000000                    IE: Unknown:
3D1606080800000000000000000000000000000000000000                    IE: Unknown:
DD0900037F01010000FF7F                    IE: Unknown:
DD0A00037F04010020000000                    IE: Unknown:
0706555320010B1B          Cell 09 - Address: <MAC address
removed>                    Channel:11                    Frequency:2.462 GHz (Channel
11)                    Quality=54/70  Signal
level=-56 dBm  
                    Encryption key:on                    ESSID:"CBCI-AC77-2.4"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 6 Mb/s                              9 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=00000089568fd536                    Extra: Last beacon: 32ms ago                    IE: Unknown:
000D434243492D414337372D322E34                    IE: Unknown:
010882848B968C129824                    IE: Unknown: 03010B                    IE: Unknown:
0706555320010B1E                    IE: Unknown: 2A0100                    IE: Unknown: 3204B048606C                    IE: Unknown:
2D1AAD011BFFFFFF00000000000000000080000000000406E6E70D00                    IE: Unknown:
331AAD011BFFFFFF00000000000000000080000000000406E6E70D00                    IE: Unknown:
3D160B000500000000000000000000000000000000000000                    IE: Unknown:
34160B000500000000000000000000000000000000000000                    IE: Unknown:
4A0E14000A002C01C800140005001900                    IE: Unknown: 7F050100000000                    IE: Unknown:
DD180050F2020101880003A4000027A4000042435E0062322F00                    IE: Unknown:
DD0900037F01010000FF7F                    IE: Unknown:
DD900050F204104A0001101044000102103B0001031047001009D9E3C17B605065A646EF67DCA02AFE10210013436973636F2053797374656D732C20496E632E102300084450433339333942102400084450433339333942104200093030303030303030311054000800060050F2040001101100084450433339333942100800020000103C0001011049000600372A000120                    IE: IEEE 802.11i/WPA2
Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) :
CCMP TKIP                        Authentication Suites
(1) : PSK                    IE: WPA Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) :
CCMP TKIP                        Authentication Suites
(1) : PSK          Cell 10 - Address: <MAC address
removed>                    Channel:11                    Frequency:2.462 GHz (Channel
11)                    Quality=39/70  Signal
level=-71 dBm  
                    Encryption key:on                    ESSID:"J6OE4"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 6 Mb/s; 9 Mb/s                              11 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=0000000126414d4f                    Extra: Last beacon: 32ms ago                    IE: Unknown: 00054A364F4534                    IE: Unknown:
010882848B0C12961824                    IE: Unknown: 03010B                    IE: Unknown:
0706555320010B1B                    IE: Unknown: 200100                    IE: Unknown: 2A0100                    IE: Unknown: 32043048606C                    IE: Unknown:
DD180050F2020101830003A4000027A4000042435E0062322F00          Cell 11 - Address: <MAC address
removed>                    Channel:11                    Frequency:2.462 GHz (Channel
11)                    Quality=39/70  Signal
level=-71 dBm  
                    Encryption key:on                    ESSID:"0UTT5"                    Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 6 Mb/s; 9 Mb/s                              11 Mb/s; 12 Mb/s;
18 Mb/s                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
```

I also disabled N and it didn't help any...
I would really appreciate any help....

---

### Post by varunendra on 2014-07-06
Welcome to Ubuntu Forums raymondabrown14!

As you can see, the formatting and lines have been completely messed in the report you have posted above. Perhaps you opened the report file in Windows and copy-pasted from there. Windows can not show Linux text files correctly due to different line ending rules. Besides, the report is incomplete.

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) This one is a modified script that covers much more info than the regular script that you ran. Instead of copy-pasting the contents from Windows, you can either attach the report file itself in the post, or copy-paste the contents into a pastebin site like pastebin.ubuntu.com, and post its link here.

**PS:**
To make a text file compatible to windows so that lines don't mess up, make sure "Line Ending" is set to "Windows" while saving the file. To do so in an already existing file, you can choose the "Save As" option of your GUI text editor in Linux/Ubuntu.

---

