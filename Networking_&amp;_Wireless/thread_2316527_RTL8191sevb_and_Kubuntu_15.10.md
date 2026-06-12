---
title: "RTL8191sevb and Kubuntu 15.10"
date: 2016-03-08
forum: Networking &amp; Wireless
---

### Post by mltriebe on 2016-03-08
Anyone have this wireless adapter working with this kernel? I have searched a lot of threads but most deal with older kernels and have been no help to me.  Wireless worked great until about a month ago when it started to have this issue. It will connect and I have wireless for 10 seconds to maybe an hour, normally it will work for a couple minutes.

I tried to install the Realtek drive but it will not compile like it did in the past.

Any help will be welcomed.

Thanks, Mike

---

### Post by chili555 on 2016-03-08
Did you try the rtlwifi-new package?```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms
```Reboot.

---

### Post by mltriebe on 2016-03-08
> **chili555 said:**
> Did you try the rtlwifi-new package?```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms
```Reboot.

No help. I installed it and rebooted 3 times and it didn't connect any of the three.

Mike

---

### Post by chili555 on 2016-03-08
Let's have a look at some diagnostics:```
sudo iwlist scan
```We only need to see your network.```
dmesg | grep -e wlp -e rtl
```

---

### Post by mltriebe on 2016-03-09
iwlist scan:
```

wlan0     Scan completed :
          Cell 01 - Address: 34:68:95:E8:78:42
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Adobe Hills"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dda9e7a8c
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000B41646F62652048696C6C73
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050700130000
                    IE: Unknown: 2D1ABD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD770050F204104A0001101044000102103B00010310470010AD55B3D52DC2120467D7570D0ECAB7F1102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180207001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 02 - Address: E0:06:E6:31:66:18
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-18-LaserJet 200 color"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000039d1487dadd
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001E48502D5072696E742D31382D4C617365724A65742032303020636F6C6F72
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101810027A4000003A4000042435E0062322F00
          Cell 03 - Address: 00:26:F2:FC:94:C6
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"wowisforfags"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000083768406b
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000C776F776973666F7266616773
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706444520010D14
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34020D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16020D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD820050F204104A0001101044000102103B00010310470010000000000000100000000026F2FC94C61021000D4E6574676561722C20496E632E1023000757504E3832344E1024000456324831104200046E6F6E651054000800060050F20400011011001457504E3832344E28576972656C65737320415029100800020086103C000103
          Cell 04 - Address: 98:FC:11:59:DD:82
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"mltriebe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000039d1804a16b
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00086D6C747269656265
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B0001031047001029CCE6942F57869A7BBCC98E28258FFE102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180208F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: 98:FC:11:59:DD:83
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"mltriebe-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000039d1804acee
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000E6D6C7472696562652D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180208F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 06 - Address: 2C:B0:5D:A4:D9:33
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"4UIOLTE8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004834b4f86cf
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00083455494F4C544538
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
          Cell 07 - Address: FA:8F:CA:32:C1:54
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2862f6140
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 05050002000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C0103FF000000000000000000000000000000000008E0E10900
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435D0062322E00
          Cell 08 - Address: 2C:B0:5D:E8:6C:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"JR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b286304818
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00024A52
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010FF21BEA41AC483F0AB916AE666CA1FE2102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 48:F8:B3:08:47:69
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Bean"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015ecf6c183
                    Extra: Last beacon: 364ms ago
                    IE: Unknown: 00044265616E
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
                    IE: Unknown: 2D1A7C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180205F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: 10:0D:7F:D5:E4:15
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"D5E415"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000010904c040185
                    Extra: Last beacon: 648ms ago
                    IE: Unknown: 0006443545343135
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180201F03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: C0:C1:C0:9E:07:06
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"YoungMaple"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006c6e5028f9
                    Extra: Last beacon: 280ms ago
                    IE: Unknown: 000A596F756E674D61706C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 12 - Address: 1C:B7:2C:75:42:48
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Kurtz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010fe5f05185
                    Extra: Last beacon: 1168ms ago
                    IE: Unknown: 00054B7572747A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050300220000
                    IE: Unknown: 2D1AAD0117FFFFFFFF00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD1E00904C0418BF0CB279830FAAFF0000AAFF0000C0050006000000C3020002
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 13 - Address: C8:D7:19:B6:83:D1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"jpaul400"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019b16501d41
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00086A7061756C343030
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001056189B8D9D5DF6A1557EB7E4B6AF603910210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30351042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: C8:D7:19:B6:83:D3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"jpaul400-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019b16502ae4
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000E6A7061756C3430302D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: C4:04:15:11:C5:77
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR03"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000590b91b919b
                    Extra: Last beacon: 900ms ago
                    IE: Unknown: 00094E4554474541523033
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A00011010440001021047001007B1D666466862F2DE3EAE65D69407FD103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: 4C:60:DE:25:7E:1E
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Harvey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000010904bf2256c
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0006486172766579
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010D3E9C0E2CE624498BC5E9910B5B83F171021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 17 - Address: C0:56:27:CF:77:FD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Info.Superhighway"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000745cde180
                    Extra: Last beacon: 1196ms ago
                    IE: Unknown: 0011496E666F2E537570657268696768776179
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001011049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: A0:63:91:B9:12:1A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR36"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b86b42d180
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 00094E4554474541523336
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001011049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: C0:C1:C0:9E:07:07
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"YoungMaple-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006c6e4b7bb8
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 0010596F756E674D61706C652D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 20 - Address: 10:0D:7F:76:7C:92
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Menchaca5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012ac23f9551
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00094D656E636861636135
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010CD2DD7E852A8352662DD003939CD71B71021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE: Unknown: DD090010180205F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.

```

and sometime after that scan it quit working and I got this scan.

```

mike@mike-Satellite-A505:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

lo        Interface doesn't support scanning.


```
```

mike@mike-Satellite-A505:~$ dmesg | grep -e wlp -e rtl
[   31.731269] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
               Loading firmware rtlwifi/rtl8192sefw.bin
[   32.222702] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   98.530382] rtlwifi:rtl_action_proc():<10000-1> sta is NULL
[  167.800066] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
mike@mike-Satellite-A505:~$ 

```

Mike

---

### Post by mltriebe on 2016-03-09
Not sure what fixed it but this is the longest it has worked for weeks.

Mike

---

