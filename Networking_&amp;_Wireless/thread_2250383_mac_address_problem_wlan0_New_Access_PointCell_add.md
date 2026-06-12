---
title: "mac address problem wlan0 New Access Point/Cell address:Not-Associated"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by wa-donraadt on 2014-10-28
I have a router with a mac address that ends with the letter "F" but iwlist and iwevent tells me that my "access point" ends with the letter "E".
How do I solve this?
see my listings:

adrian@adrian:~$ sudo iwevent
Waiting for Wireless Events from interfaces...
15:55:33.559527   wlan0    Set Mode:Managed
15:55:33.559681   wlan0    Set Frequency:2.447 GHz (Channel 8)
15:55:33.559749   wlan0    Set ESSID:"FRITZ!Box Fon WLAN 7360"
15:55:34.194631   wlan0    New Access Point/Cell address:  :  :  :  :  :BE
15:55:44.207899   wlan0    New Access Point/Cell address:Not-Associated
15:55:44.211005   wlan0    Set ESSID:"\x02\x1A\xFEC\xFB\xFA\xAA:\xFB)\xD1\xE6\x05<|\x94u\xD8\xBEa\x89\xF9\\xBB\xA8\x99\x0F\x95\xB1\xEB\xF1\xB3"

adrian@adrian:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address:   :  :  :  :  :BE
                    ESSID:"FRITZ!Box Fon WLAN 7360"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037333630
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE111BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 331AEE111BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1608080400000000000000000000000000000000000000
                    IE: Unknown: 341608080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F050100000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD650050F204104A0001101044000102103B0001031047001016F456042F6062ED842BC025066AAABE1021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800022388103C000103

---

