---
title: "Weak wireless"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by SilentOnee on 2013-09-15
Hello,

For some reason I can hardly connect to my wireless network. Sometimes it connects for about 5-30 minutes, but then disconnects and struggles to get back online. I tried placing my laptop near my router, however it still wouldn't connect! Any help would be okay, I do not know which codes to post, so please let me know how I can help.

It works for all my other devices, but not for this laptop so I doubt it's a problem with the router... 

Thanks!

---

### Post by Hadaka on 2013-09-15
Hi, please post the output of..
```
iwconfig
lspci -nn | grep 0280
```
thanks.

---

### Post by SilentOnee on 2013-09-15
I am using ethernet on the same laptop to post this, if you needed to know. :P

iwconfig:
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```

lspci -nn | grep 0280:
```

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

```

---

### Post by Hadaka on 2013-09-15
thanks, if possible from the wireless connection please do
and post..
```
iwconfig
sudo iwlist wlan0 scan
```
I'm wanting to see the signal strength and then proceed.
thanks.

---

### Post by SilentOnee on 2013-09-15
It was refusing to connect to wireless at all, however a restart allowed me to connect to it.

iwconfig:
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TELUS4688"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:26:88:E5:AE:DC   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

```

sudo iwlist wlan0 scan:
```

          Cell 01 - Address: 00:26:88:E5:AE:DC
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-4 dBm  
                    Encryption key:on
                    ESSID:"TELUS4688"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000144814e3f78
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000954454C555334363838
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1604080400000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B00010310470010519DAB3D732B6ECB00E0F125FA271C5F1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404080400000000000000000000000000000000000000
          Cell 02 - Address: 5C:D9:98:69:F8:5E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"vcam_rr"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008ca99e040
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00077663616D5F7272
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 28:10:7B:61:2B:F4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"CN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000214eb6dde04
                    Extra: Last beacon: 988ms ago
                    IE: Unknown: 0002434E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555349010B1E
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: Unknown: 0505000100801E
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C1846470900
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0505001A127A
                    IE: Unknown: DD07000C4317000000
          Cell 04 - Address: A8:39:44:51:AE:24
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"TELUS0246"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c5d52dd8d7
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000954454C555330323436
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B00010310470010DF6AD079D60B44B8EA46E3C4DFD57B2F1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
          Cell 05 - Address: 78:CD:8E:C4:8E:69
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-4 dBm  
                    Encryption key:on
                    ESSID:"C48E65"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008afc9d8053
                    Extra: Last beacon: 308ms ago
                    IE: Unknown: 0006433438453635
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 0504000100A0
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1608000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
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
                    IE: Unknown: 0B05030008127A
                    IE: Unknown: DD07000C4304000000
          Cell 06 - Address: C8:BE:19:60:5A:90
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"dlink-5A90"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e264f8034b
                    Extra: Last beacon: 22012ms ago
                    IE: Unknown: 000A646C696E6B2D35413930
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 0505000100D003
                    IE: Unknown: DD360050F204104A0001101044000102105700010110470010BC329E001DD811B28601C8BE19605A90103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1013FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05080068127A
                    IE: Unknown: DD07000C4300000000
          Cell 07 - Address: 38:60:77:F5:88:5E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Skynet2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000036ab2459186
                    Extra: Last beacon: 21996ms ago
                    IE: Unknown: 0007536B796E657432
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 98:FC:11:7A:4A:03
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"murdoch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000164df05618f
                    Extra: Last beacon: 172ms ago
                    IE: Unknown: 00076D7572646F6368
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 09 - Address: 5C:D9:98:6B:8C:9A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-6 dBm  
                    Encryption key:on
                    ESSID:"Tresspassers will be shot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000bfe68d80
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 00195472657373706173736572732077696C6C2062652073686F74
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001900000000000000000000000000000000000000
                    IE: Unknown: 3D160B001900000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD270050F204104A000110104400010210470010000000000000100000005CD9986B8C9A103C000103
          Cell 10 - Address: A8:39:44:41:A3:80
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"TELUS1432"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000fa975ec5072
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000954454C555331343332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B00010310470010F8187EEA19B861B913FE509097500ED51021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 11 - Address: 00:14:D1:44:EE:22
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"TRENDnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b666f51538b
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 00085452454E446E6574
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: 6C6C00032F0100011800158B000000000100A8394448890800000000000000001000058B00000000010000000000
          Cell 12 - Address: A8:39:44:48:89:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Telus2789"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009cff6a62a6
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000954656C757332373839
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B00010310470010669676C0972224247F4800175DF5DB1E1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080400000000000000000000000000000000000000



```

---

### Post by Hadaka on 2013-09-16
Hi, is this YOUR essid? "
ESSID:"Tresspassers will be shot"?
if so..you might want to rename and remove the spaces.

---

### Post by SilentOnee on 2013-09-16
That is not mine, my ESSID is TELUS4688.

---

### Post by Hadaka on 2013-09-16
ok, you have an excellent signal..
 Quality=70/70

try changing from channel 4 to channel 1 or 11
that should show some improvement.

please also post the output of..
```
modinfo rtl8723e
```
thanks.

---

### Post by SilentOnee on 2013-09-16
I have switched to channel 11; I will let you know of the progress as I use internet.
modinfo rtl8723e:
```

ERROR: modinfo: could not find module rtl8723e

```

Edit: Both 1 and 11 are giving me disconnections or dropped connection.

---

### Post by Hadaka on 2013-09-16
ok, please post from the wireless connection.
```
lspci -nnk | grep 0280
```
we're gettin there...

---

### Post by SilentOnee on 2013-09-16
lspci -nnk | grep 0280:
```

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

```

---

### Post by Hadaka on 2013-09-16
thanks, I should have also asked to see..
```
lsmod
```
lets see what driver you are currently using.
thanks for hanging in there.

---

### Post by SilentOnee on 2013-09-16
No worries, I truly appreciate the help!

lsmod
```

Module                  Size  Used by
vesafb                 13876  1 
bnep                   18258  2 
parport_pc             28284  0 
ppdev                  17113  0 
rfcomm                 47864  12 
joydev                 17613  0 
fglrx                6728820  170 
snd_hda_codec_realtek    79916  1 
kvm                   455932  0 
arc4                   12573  2 
snd_hda_codec_hdmi     37434  1 
ghash_clmulni_intel    13259  0 
snd_hda_intel          44339  5 
rtl8723ae              88995  0 
snd_hda_codec         141716  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtlwifi                81225  1 rtl8723ae
snd_hwdep              13668  1 snd_hda_codec
aesni_intel            55495  2 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              630977  1 rtlwifi
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
uvcvideo               82214  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97873  0 
cfg80211              525244  2 rtlwifi,mac80211
snd                    69533  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13890  0 
videobuf2_core         40785  1 uvcvideo
wmi                    19256  0 
btusb                  22431  0 
videodev              130053  2 uvcvideo,videobuf2_core
toshiba_bluetooth      12852  0 
serio_raw              13215  0 
bluetooth             247024  24 bnep,rfcomm,btusb
videobuf2_vmalloc      13056  1 uvcvideo
i2c_piix4              13459  0 
soundcore              12680  1 snd
videobuf2_memops       13202  1 videobuf2_vmalloc
video                  19652  0 
lp                     17799  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
amd_iommu_v2           19198  1 fglrx
mac_hid                13253  0 
microcode              23017  0 
k10temp                13173  0 
ahci                   25879  2 
libahci                31606  1 ahci
r8169                  68716  0 

```

---

### Post by Hadaka on 2013-09-16
thanks..your driver is rtl8723ae
let's give this a try..please do..
```
sudo modprobe -rfv rtl8192ae
sudo modprobe -v rtl8192ae swenc=1
```
dont boot and let the wireless connection run for an hour or so.
*IF it imporves and does NOT drop out
then do.
```
echo "options rtl8192ae swenc=1" > /etc/modprobe.d/rtl8192ae.conf
```

what this does is removes the N speed which is a typical problem for linux.
also...*IF this does help, then try again channels 1 or 11
report back after your changes and findings.
thanks.

---

### Post by SilentOnee on 2013-09-16
I get this for both of the commands:
```

FATAL: Module rtl8192ae not found.

```

Is that supposed to happen?

---

### Post by Hadaka on 2013-09-16
yes it is,,because i need to correct the commands i gave you.
they should be...
```
sudo modprobe -rfv rtlwifi
sudo modprobe -v rtlwifi swenc=1
```
let run for an hour..
then..if no dropouts..
```
echo "options rtlwifi swenc=1" > /etc/modprobe.d/rtlwifi.conf
```
sorry about that.

---

### Post by Hadaka on 2013-09-16
yes it is,,because i need to correct the commands i gave you.
they should be...
```
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae swenc=1
```
let run for an hour..
then..if no dropouts..
```
echo "options rtl8723ae swenc=1" > /etc/modprobe.d/rtl8723ae.conf
```
sorry about that.
***IGNORE POST #16***

---

### Post by SilentOnee on 2013-09-16
Uh oh..

```

FATAL: Module rtlwifi is in use.

```

Edit: Going to bed for the day, will continue tomorrow; thanks for the help. :)

---

### Post by Hadaka on 2013-09-16
me also..im noddng off here and not thinking...read post 17 please.

---

### Post by SilentOnee on 2013-09-16
sudo modprobe -rfv rtl8723ae:
```

rmmod /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
rmmod /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
rmmod /lib/modules/3.8.0-30-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-30-generic/kernel/net/wireless/cfg80211.ko

```

sudo modprobe -v rtl8723ae swenc=1:
```

insmod /lib/modules/3.8.0-30-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko swenc=1

```

I think it worked! I timed an hour before I used the commands and I had about a dropped connection every 2-5 minutes. After the commands the amount of dropped connections decreased by a lot. In an hour I had about 3 dropped connections, which is a HUGE improvement. So, I went ahead and did the final command but I get a permission error:

```

bash: /etc/modprobe.d/rtl8723ae.conf: Permission denied

```

---

### Post by Hadaka on 2013-09-16
Hi, here is the correct command...
```
sudo su
echo "options rtl8723ae swenc=1" > /etc/modprobe.d/rtl8723ae.conf
exit 0

```
I apologize for being 1/2 awake with some of these commands.
hope this helps.

---

### Post by SilentOnee on 2013-09-16
No problem, I'm just glad I can finally browse the internet without getting a headache!
Thanks for all your help, will mark the thread as solved. :D

---

