---
title: "No internet or web access despite lan/wifi connection"
date: 2022-05-21
forum: Networking &amp; Wireless
---

### Post by eriolbrumel on 2022-05-21
Hello,


I am completely at a loss: On my notebook with current Kubuntu 22.04 WLAN and the Lan connection works, but I can't get on the Internet. Ping does not work, I suspect it has to do with DNS, but I can't get to my Fritzbox either. BTW: I have a Windows 11 dual boot, and there internet still works.


I have attached a few outputs below, but I can't find the problem.


I have not knowingly changed anything. But: Since the update from 21.10 to 22.04 nordvpn did not work for me, I was logged in but could not connect. So I wanted to see if a firewall (ufw) is running and blocking nordvpn, and I enabled ufw once and disabled it again. But what I can have broken by this I do not know ... After that the internet did not work anymore.


Help! Does anyone have an idea?


Greetings
Eriol

```
bogislav@Messiah:~$ uname -a
Linux Messiah 5.15.0-30-generic #31-Ubuntu SMP Thu May 5 10:00:34 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
bogislav@Messiah:~$ ifconfig -a
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.178.61  netmask 255.255.255.0  broadcast 192.168.178.255
        ether 84:a9:3e:0e:fb:1d  txqueuelen 1000  (Ethernet)
        RX packets 427  bytes 81788 (81.7 KB)
        RX errors 0  dropped 179  overruns 0  frame 0
        TX packets 106  bytes 21103 (21.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Lokale Schleife)
        RX packets 641  bytes 75310 (75.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 641  bytes 75310 (75.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.178.22  netmask 255.255.255.0  broadcast 192.168.178.255
        inet6 fe80::f2ab:2a3c:f867:f437  prefixlen 64  scopeid 0x20<link>
        ether 80:2b:f9:73:c2:13  txqueuelen 1000  (Ethernet)
        RX packets 369  bytes 56387 (56.3 KB)
        RX errors 0  dropped 139  overruns 0  frame 0
        TX packets 6  bytes 859 (859.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


bogislav@Messiah:~$ iwconfig
lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11  ESSID:"Nemesis"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 3C:A6:2F:86:65:53   
          Bit Rate=292.5 Mb/s   Tx-Power=23 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


bogislav@Messiah:~$ route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 eno1
0.0.0.0         192.168.178.1   0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.178.0   0.0.0.0         255.255.255.0   U     100    0        0 eno1
192.168.178.0   0.0.0.0         255.255.255.0   U     600    0        0 wlo1
bogislav@Messiah:~$ arp -av
? (192.168.178.30) auf 30:05:5c:5f:eb:7d [ether] auf eno1
_gateway (192.168.178.1) auf 2c:91:ab:5f:47:91 [ether] auf eno1
Einträge: 2   Ignoriert: 0   Gefunden: 2
bogislav@Messiah:~$ ip neigh show
192.168.178.30 dev eno1 lladdr 30:05:5c:5f:eb:7d STALE
192.168.178.1 dev eno1 lladdr 2c:91:ab:5f:47:91 STALE


bogislav@Messiah:~$ ping -c 2 $(route -n | grep UG | awk {'print $2'})
PING 192.168.178.1 (192.168.178.1) 56(124) bytes of data.


--- 192.168.178.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1018ms


bogislav@Messiah:~$ ping -c 2 www.spiegel.de
ping: www.spiegel.de: Temporärer Fehler bei der Namensauflösung


bogislav@Messiah:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
bogislav@Messiah:~$ sudo iwlist scan
lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


wlo1      Scan completed :
          Cell 01 - Address: 2C:91:AB:5F:47:93
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Nemesis"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000898af039
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 00074E656D65736973
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030134
                    IE: Unknown: 050400010000
                    IE: Unknown: 073C4445202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E78011E7C011E80011E84011E88011E8C011E
                    IE: Unknown: 200103
                    IE: Unknown: 0B050300090000
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AEF0903FFFFFFFF00000000000000000100000000000000000000
                    IE: Unknown: 3D1634050400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0000000040
                    IE: Unknown: BF0CFA798B33AAFF0000AAFF0020
                    IE: Unknown: C005013A32FCFF
                    IE: Unknown: C1060200FFD40000
                    IE: Unknown: C305032E2E2E2E
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD088CFDF00101020100
                    IE: Unknown: DD168CFDF0040000494C5103020972018C16000046000000
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD0700037F05010001
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001031049000600372A000120
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1F8CFDF00000010100000101000000000000FFFF2C91AB5F4793000000000000
          Cell 02 - Address: 2E:91:AB:5F:47:93
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Nemesis Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000898af039
                    Extra: Last beacon: 104ms ago
                    IE: Unknown: 000D4E656D65736973204775657374
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030134
                    IE: Unknown: 050400010000
                    IE: Unknown: 073C4445202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E78011E7C011E80011E84011E88011E8C011E
                    IE: Unknown: 200103
                    IE: Unknown: 0B050000090000
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AEF0903FFFFFFFF00000000000000000100000000000000000000
                    IE: Unknown: 3D1634050400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0000000040
                    IE: Unknown: BF0CFA798B33AAFF0000AAFF0020
                    IE: Unknown: C005013A32FCFF
                    IE: Unknown: C1060000FFD40000
                    IE: Unknown: C305032E2E2E2E
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD088CFDF00101020100
                    IE: Unknown: DD168CFDF0040000494C5103020972018C16000046000000
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD0700037F05010001
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001031049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : PSK unknown (8)
          Cell 03 - Address: 3C:A6:2F:86:65:52
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Nemesis"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009dc6f94923
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 00074E656D65736973
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 0B050300120000
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AAD0903FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0000000040
                    IE: Unknown: BF0CB2598933FAFF0000FAFF0020
                    IE: Unknown: C005000000FCFF
                    IE: Unknown: C1060100F2310000
                    IE: Unknown: DD1A00904C0408BF0CB2598933FAFF0000FAFF0020C005000000FCFF
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD168CFDF0040000494C51030209720100000000EF120000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B00010310470010A1FE040AFBCF0622AE93862FA63C52651021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020280103C0001031049000600372A000120
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD088CFDF00101020100
          Cell 04 - Address: 2C:91:AB:5F:47:94
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Nemesis"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000088a0d2d6
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 00074E656D65736973
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 0B050300160000
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AAD0903FFFFFFFF00000000000000000100000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0000000040
                    IE: Unknown: BF0CB2798B33AAFF0000AAFF0020
                    IE: Unknown: C005000000FCFF
                    IE: Unknown: C1060200FEE20000
                    IE: Unknown: DD1A00904C0408BF0CB2798B33AAFF0000AAFF0020C005000000FCFF
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD168CFDF0040000494C5103020972018C16000046000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B00010310470010B18931F24734767547892C91AB5F47931021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020280103C0001031049000600372A000120
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1F8CFDF00000010100000101000000000000FFFF0000000000002C91AB5F4794
                    IE: Unknown: DD088CFDF00101020100
          Cell 05 - Address: 3E:A6:2F:86:65:52
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Nemesis Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009dc6f8a20e
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000D4E656D65736973204775657374
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 0B050000120000
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AAD0903FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0000000040
                    IE: Unknown: BF0CB2598933FAFF0000FAFF0020
                    IE: Unknown: C005000000FCFF
                    IE: Unknown: C1060000F2310000
                    IE: Unknown: DD1A00904C0408BF0CB2598933FAFF0000FAFF0020C005000000FCFF
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD168CFDF0040000494C51030209720100000000EF120000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700109E82321DBC0C2F19378E6C4A41F079BF1021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020280103C0001031049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : PSK unknown (8)
                    IE: Unknown: DD088CFDF00101020100
          Cell 06 - Address: 8C:85:80:A1:FB:D6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000033ad56f1a1
                    Extra: Last beacon: 7640ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 7F09010000000000000000
                    IE: Unknown: DD180050F20201010000022200002222000042225E0062222F00
                    IE: Unknown: 0B0503000F127A
                    IE: Unknown: DD07000C4300000000
          Cell 07 - Address: 3C:A6:2F:86:65:53
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Nemesis"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009dc6eeab13
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 00074E656D65736973
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 073C4445202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E78011E7C011E80011E84011E88011E8C011E
                    IE: Unknown: 0B050300030000
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AEF0903FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1624050400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0000000040
                    IE: Unknown: BF0CB2598933FAFF0000FAFF0020
                    IE: Unknown: C005012A00FCFF
                    IE: Unknown: C106030000740000
                    IE: Unknown: C304022E2E2E
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD168CFDF0040000494C51030209720100000000EF120000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B00010310470010A1FE040AFBCF0622AE93862FA63C52651021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020280103C0001031049000600372A000120
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD088CFDF00101020100
          Cell 08 - Address: 3E:A6:2F:86:65:53
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Nemesis Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009dc6ede65a
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000D4E656D65736973204775657374
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 073C4445202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E78011E7C011E80011E84011E88011E8C011E
                    IE: Unknown: 0B050000030000
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AEF0903FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1624050400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0000000040
                    IE: Unknown: BF0CB2598933FAFF0000FAFF0020
                    IE: Unknown: C005012A00FCFF
                    IE: Unknown: C106000000740000
                    IE: Unknown: C304022E2E2E
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD168CFDF0040000494C51030209720100000000EF120000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700109E82321DBC0C2F19378E6C4A41F079BF1021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020280103C0001031049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : PSK unknown (8)
                    IE: Unknown: DD088CFDF00101020100


                    
bogislav@Messiah:~$ sudo systemctl status systemd-resolved
&#9679; systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-05-21 17:27:41 CEST; 15min ago
       Docs: man:systemd-resolved.service(8)
             man:org.freedesktop.resolve1(5)
             https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers
             https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients
   Main PID: 934 (systemd-resolve)
     Status: "Processing requests..."
      Tasks: 1 (limit: 9213)
     Memory: 8.4M
        CPU: 9.585s
     CGroup: /system.slice/systemd-resolved.service
             &#9492;&#9472;934 /lib/systemd/systemd-resolved


Mai 21 17:27:40 Messiah systemd-resolved[934]: Using system hostname 'Messiah'.
Mai 21 17:27:41 Messiah systemd[1]: Started Network Name Resolution.
Mai 21 17:27:45 Messiah systemd-resolved[934]: eno1: Bus client set search domain list to: fritz.box
Mai 21 17:27:45 Messiah systemd-resolved[934]: eno1: Bus client set default route setting: yes
Mai 21 17:27:45 Messiah systemd-resolved[934]: eno1: Bus client set DNS server list to: 192.168.178.1, fd00::2e91:abff:fe5f:4791
Mai 21 17:27:46 Messiah systemd-resolved[934]: Using degraded feature set UDP instead of UDP+EDNS0 for DNS server 192.168.178.1.
Mai 21 17:28:02 Messiah systemd-resolved[934]: wlo1: Bus client set search domain list to: fritz.box
Mai 21 17:28:02 Messiah systemd-resolved[934]: wlo1: Bus client set default route setting: yes
Mai 21 17:28:02 Messiah systemd-resolved[934]: wlo1: Bus client set DNS server list to: 192.168.178.1
Mai 21 17:32:47 Messiah systemd-resolved[934]: Grace period over, resuming full feature set (UDP+EDNS0) for DNS server 192.168.178.1.



```

---

### Post by frm77000 on 2022-05-24
H Eriol
Try to disable the wifi card and test only with the ethernet cable.
Then reverse using only wifi and try again

Let us know

F.

---

