---
title: "Network mgr repeatedly asks for credential"
date: 2014-04-06
forum: Networking &amp; Wireless
---

### Post by suphavitp on 2014-04-06
I am using kernel 3.11.0 with gnome shell. Everyday I connect to WPA2 enterprise network and get disconnected every hour or so. Title sums up my problem. How do I fix this?
Similar thread: [http://ubuntuforums.org/showthread.php?t=2137174](http://ubuntuforums.org/showthread.php?t=2137174)

---

### Post by varunendra on 2014-04-10
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by suphavitp on 2014-04-11
```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


##### kernel #####


Linux J 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1483]
	Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:1426]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 003: ID 064e:f203 Suyin Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: yes
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


eth1      IEEE 802.11abg  ESSID:"UCLA_SECURE_RES"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         169.232.245.5   0.0.0.0         UG    0      0        0 eth1
169.232.245.0   0.0.0.0         255.255.255.0   U     9      0        0 eth1


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


- Device: eth1  [UCLA_SECURE_RES] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    HP-Print-E4-Photosmart 5520: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    HP-Print-5D-Photosmart 5520: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    HP-Print-1C-Photosmart 6520: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 89
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
    HP-Print-2A-Photosmart 5520: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    HP-Print-FC-ENVY 4500 series: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15
    HP-Print-21-ENVY 4500 series: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    HP-Print-8E-Deskjet 3510 series: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Ian and Feli's Network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 71
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    *UCLA_SECURE_RES:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2 Enterprise
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2 Enterprise
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    HP-Print-C2-Officejet 4630: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27


  IPv4 Settings:
    Address:         169.232.245.64
    Prefix:          24 (255.255.255.0)
    Gateway:         169.232.245.5


    DNS:             164.67.128.1
    DNS:             128.97.128.1
    DNS:             164.67.128.3


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


eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-2A-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001B48502D5072696E742D32412D50686F746F736D6172742035353230
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-E4-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001B48502D5072696E742D45342D50686F746F736D6172742035353230
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 21552ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 21552ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-22-Photosmart 6520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001B48502D5072696E742D32322D50686F746F736D6172742036353230
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD7708000900040000001701020100020178031650686F746F736D617274203635323020736572696573040F36353235000000000000000F54483305105448334245343630514830355850000006101C852A4DB8001F08ABCDA0D3C1C2FA220704A9E84978080200D4090200080A04000000010B0400000000
          Cell 17 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-5D-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001B48502D5072696E742D35442D50686F746F736D6172742035353230
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 18 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 19 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 20 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 21 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-21-ENVY 4500 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001C48502D5072696E742D32312D454E5659203435303020736572696573
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD89080009000400000007010201000201780328454E5659203435303020736572696573000000000000000000000000000000000000000000000000040F34353030000000000000000F434E330510434E333739315033583130355834000006101C852A4DB8001F08ABCDA45D369E36210704A9E8BBB7080200D4090200080A04000000010B0400000000


##### iwlist channel #####


eth1      26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### lsmod #####


wl                   4207760  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              480503  1 wl


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     F09EC4762307349676747C4
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


##### modules #####


lp
rtc


##### blacklist #####


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


##### udev rules #####


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[   15.681322] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.685095] wl: module verification failed: signature and/or required key missing - tainting kernel
[   15.724442] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   15.730046] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[  246.502915] ERROR @wl_dev_intvar_get : error (-1)
[  246.502924] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  391.181955] ERROR @wl_dev_intvar_get : error (-1)
[  391.181961] ERROR @wl_cfg80211_get_tx_power : error (-1)


########## wireless info END ############

```
Yes, I am connected to the network in question.

---

### Post by varunendra on 2014-04-11
Please try the native "brcmsmac" driver by getting rid of the proprietary (sta) driver that you are currently using.

To purge the current sta driver and its settings, please open a terminal (Ctrl-Alt-T) and run the following command -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot and check the loaded drivers with the following command -
```
lsmod | egrep 'brcm|wl|ssb'
```
You should see only "brcmsmac" and its supporting drivers, no "wl", no "ssb" in the output. If so, is the connectivity any better?

Some users have reported problems with the native driver included in the kernel version that you are using. If that happens to be the case with you too, we may try a newer version, but _ONLY_ if required!

---

### Post by suphavitp on 2014-04-12
for some reason I can still see "ssb" from runnung lsmod
```

brcmsmac              562904  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              597268  2 b43,brcmsmac
cfg80211              480503  3 b43,brcmsmac,mac80211
[COLOR=#ff0000]ssb[/COLOR]                    62057  1 b43
bcma                   46699  3 b43,brcmsmac



```

---

### Post by varunendra on 2014-04-12
Because b43 is loading as well. Let's blacklist only these two drivers manually. Please open a terminal and run the following command in it -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and recheck the lsmod command. Are b43 and ssb still there? If not, is the connectivity any better?

---

### Post by suphavitp on 2014-04-15
I have done what you said and used the network for a day now. Although the frequency of network mgr prompt decreased noticeably, it still asks for credential every few hours. Is that expected?

---

### Post by varunendra on 2014-04-16
> **suphavitp said:**
> Although the frequency of network mgr prompt decreased noticeably, it still asks for credential every few hours. Is that expected?

No it's not. We expect the "brcmsmac" driver to work pretty smoothly with BCM4313 card. Could you please post a fresh report of the "wireless_script"?

The version of brcmsmac driver included by default in kernel 3.11 seems to have some problems sometimes as reported by some users. So **_IF_** everything else is okay, we may try compiling a newer version of the driver to get hopefully the best performance possible with the card.

To determine whether everything else is at its optimal setting or not, I need to see the current status of the overall setup which the wireless_script may provide.

---

### Post by suphavitp on 2014-04-16
Here goes
```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


##### kernel #####


Linux J 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1483]
	Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:1426]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 003: ID 064e:f203 Suyin Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"UCLA_WIFI_RES"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:72   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         149.142.229.5   0.0.0.0         UG    0      0        0 wlan0
149.142.229.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0


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


- Device: wlan0  [UCLA_WIFI_RES] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    HP-Print-E4-Photosmart 5520: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2
    HP-Print-80-Photosmart 5520: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA2
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    HP-Print-5D-Photosmart 5520: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57
    HP-Print-2A-Photosmart 5520: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    *UCLA_WIFI_RES:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    TwoTwelve:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    UCLA_SECURE_RES: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    UCLA_WEB_RES:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    UCLA_WIFI_RES:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27


  IPv4 Settings:
    Address:         149.142.229.175
    Prefix:          24 (255.255.255.0)
    Gateway:         149.142.229.5


    DNS:             164.67.128.3
    DNS:             164.67.128.1
    DNS:             128.97.128.1


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
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057040d0f4c
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057040d0e1c
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057040d107c
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-E4-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057486a64c6
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 001B48502D5072696E742D45342D50686F746F736D6172742035353230
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003caa0fad21
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003caa2214e2
                    Extra: Last beacon: 420ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040814
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003caa0faf95
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-5D-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d6f764ba0
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 001B48502D5072696E742D35442D50686F746F736D6172742035353230
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a760c6180
                    Extra: Last beacon: 28440ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040814
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a760c639c
                    Extra: Last beacon: 28440ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040814
          Cell 11 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005746ce91a9
                    Extra: Last beacon: 27524ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000574871e03c
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000574871e187
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"TwoTwelve"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000007e5e9a65177
                    Extra: Last beacon: 28164ms ago
                    IE: Unknown: 000954776F5477656C7665
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400030100
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016B0B20
                    IE: Unknown: DD0E0017F2070001010668A86D5F62A9
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-2A-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000574afcd30b
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 001B48502D5072696E742D32412D50686F746F736D6172742035353230
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005748d494e0
                    Extra: Last beacon: 27580ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040812
          Cell 17 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005748d495ed
                    Extra: Last beacon: 27580ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040812
          Cell 18 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000574b0380ff
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 19 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000574b03822f
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 20 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000574b038360
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 21 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WEB_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057028b9b97
                    Extra: Last beacon: 27524ms ago
                    IE: Unknown: 000C55434C415F5745425F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 22 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"UCLA_WIFI_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057028b9e02
                    Extra: Last beacon: 27524ms ago
                    IE: Unknown: 000D55434C415F574946495F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 23 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"UCLA_SECURE_RES"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057028ba06d
                    Extra: Last beacon: 27524ms ago
                    IE: Unknown: 000F55434C415F5345435552455F524553
                    IE: Unknown: 01088C1298243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


##### iwlist channel #####


wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### lsmod #####


brcmsmac              562904  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              597268  1 brcmsmac
cfg80211              480503  2 brcmsmac,mac80211
bcma                   46699  2 brcmsmac


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


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
blacklist b43
blacklist ssb


##### udev rules #####


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[   16.701447] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   16.701476] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   16.701499] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   16.701544] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   16.714896] bcma: bus0: Bus registered
[   17.740241] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[   17.802553] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   24.530869] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   24.530882] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   24.531035] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.531416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.924460] wlan0: authenticate with <MAC address removed>
[   25.925381] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.926805] wlan0: authenticated
[   25.927528] wlan0: associate with <MAC address removed> (try 1/3)
[   25.930817] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[   25.931298] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   25.931301] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   25.931309] wlan0: associated
[   25.931330] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.458247] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)


########## wireless info END ############

```

---

### Post by varunendra on 2014-04-18
Channels 1 and 6 seem pretty crowded. If you can, please try changing the channel in the desired Access-Point to 11. Reboot the AP after saving the change.

If that doesn't help, here's how to compile and install the newer driver -

First, make sure the essential packages for building a driver are already installed -
```
sudo apt-get install linux-headers-generic build-essential
```

Then,

[indent]**1)** Download the "backports-3.12.8-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Right-click the downloaded package > click "Extract here". This will extract the contents of the downloaded archive into a directory of the same name as the downloaded archive.

**3)** Now open a terminal, and assuming this extracted directory is in the **Downloads** directory within your Home directory, please run the following commands to compile and install the driver -
```
cd Downloads/backports-3.12.8-1
make defconfig-brcmsmac
make
sudo make install
```
Let the process finish and watch out for errors. Report back if there are any.[/indent]

If everything finishes smoothly, reboot, and check the connectivity. Let us know if things are improved. If not, you may try the same process as steps 1-3 above with versions newer than 3.12.8-1 (downloaded from the same page), I recommended that one because it is a tested version and so far it has always worked better whenever I recommended it to someone.

---

### Post by suphavitp on 2014-04-24
Sorry for the late reply. I have done as you suggested and used the network for about half a day now. No problem encountered. I think we can consider the issue solved. Thank you so much for taking time to help me out.

---

### Post by varunendra on 2014-04-24
You're welcome!

It's always so pleasant to see a positive feedback. :) *[COLOR="#696969"](although experience has taught me to be always ready for surprises!)[/COLOR]*

---

