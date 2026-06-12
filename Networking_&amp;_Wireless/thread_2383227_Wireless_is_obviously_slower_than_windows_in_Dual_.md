---
title: "Wireless is obviously slower than windows in Dual system"
date: 2018-01-22
forum: Networking &amp; Wireless
---

### Post by tongmengwan on 2018-01-22
[SIZE=4]I have Dell M6500. I am new user of Linux. 
Dual system: Windows 7 Ultimate
                    Ubuntu 16.04 LTS

Test internet speed at : [http://www.speedtest.net/](http://www.speedtest.net/)

In Windows, speed goes  about 90-100mbps
In Linux, it is about 25-30.


[FONT=Calibri]I used: [/FONT][FONT=Calibri]lshw[/FONT][FONT=Calibri] -c network[/FONT][/SIZE][FONT=Calibri][SIZE=4] to following information. 
Can anyone help me resolve this problem? 

According to suggestion of  wildmanne39, I posted following information about 
my network. 
[/SIZE][/FONT]
						[FONT=Calibri][SIZE=4]https://paste.ubuntu.com/26455083/

Thank you !
[/SIZE]
----------------------------------------------------------------
[/FONT][LEFT][COLOR=windowtext][FONT=Calibri]WARNING: you should run this program as super-user.[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]  *-network               [/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       description: Wireless interface[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       product: Centrino Advanced-N + WiMAX 6250 [Kilmer Peak][/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       vendor: Intel Corporation[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       physical id: 0[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       bus info: [/FONT][COLOR=#0563C1][FONT=Calibri]_pci@0000:0c:00.0_[/FONT][/COLOR]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       logical name: wlp12s0[/FONT][/COLOR]
[COLOR=windowtext][FONT=Calibri]       version: 5e[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       serial: [/FONT][FONT=Calibri]64:80:99:43:3[/FONT][FONT=Calibri]e:d4[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       width: 64 bits[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       clock: 33MHz[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       capabilities: [/FONT][FONT=Calibri]bus_master[/FONT][FONT=Calibri]cap_list[/FONT][FONT=Calibri] ethernet physical wireless[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       configuration: broadcast=yes driver=[/FONT][FONT=Calibri]iwlwifi[/FONT][FONT=Calibri]driverversion[/FONT][FONT=Calibri]=4.4.0-109-generic firmware=41.28.5.1 build 33926 [/FONT][FONT=Calibri]ip[/FONT][FONT=Calibri]=192.168.1.122 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       resources: irq:39 [/FONT][FONT=Calibri]memory:f[/FONT][FONT=Calibri]1ffe000-f1ffffff[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]  *-network[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       description: Ethernet interface[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       product: [/FONT][FONT=Calibri]NetXtreme[/FONT][FONT=Calibri] BCM5761e Gigabit Ethernet [/FONT][FONT=Calibri]PCIe[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       vendor: Broadcom Corporation[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       physical id: 0[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       bus info: [/FONT][COLOR=#0563C1][FONT=Calibri]_pci@0000:09:00.0_[/FONT][/COLOR]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       logical name: eno1[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       version: 10[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       serial: f0:4[/FONT][FONT=Calibri]d:a[/FONT][FONT=Calibri]2:60:1a:17[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       capacity: 1Gbit/s[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       width: 64 bits[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       clock: 33MHz[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       capabilities: [/FONT][FONT=Calibri]bus_master[/FONT][FONT=Calibri]cap_list[/FONT][FONT=Calibri] ethernet physical [/FONT][FONT=Calibri]tp[/FONT][FONT=Calibri] 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd [/FONT][FONT=Calibri]autonegotiation[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       configuration: [/FONT][FONT=Calibri]autonegotiation[/FONT][FONT=Calibri]=on broadcast=yes driver=tg3 [/FONT][FONT=Calibri]driverversion[/FONT][FONT=Calibri]=3.137 firmware=5761e-v3.71 latency=0 link=no multicast=yes port=twisted pair[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       resources: irq:41 [/FONT][FONT=Calibri]memory:f[/FONT][FONT=Calibri]1be0000-f1beffff memory:f1bf0000-f1bfffff[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]  *-network DISABLED[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       description: Ethernet interface[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       physical id: 1[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       logical name: enx001de14bd9fe[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       serial: 00:1[/FONT][FONT=Calibri]d:e[/FONT][FONT=Calibri]1:4b:d9:fe[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       capabilities: ethernet physical[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.[/FONT][FONT=Calibri]5.sbcf[/FONT][FONT=Calibri] link=no[/FONT]
[/COLOR]
[COLOR=windowtext][FONT=Calibri]WARNING: output may be incomplete or inaccurate, you should run this program as super-user.[/FONT][FONT=Calibri] 
[/FONT][/COLOR][/LEFT]

---

### Post by chili555 on 2018-01-22
We would also like to see:```
sudo iwlist scan
```Just show us your access points and please redact the MAC addresses like this:```
wlp3s0    Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]xx:2B:B0:DC:45:zz[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001063af09824
                    Extra: Last beacon: 784ms ago
                    IE: Unknown: <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

---

### Post by tongmengwan on 2018-01-22
```
lo        Interface doesn't support scanning.


wlp12s0   Scan completed :
          Cell 01 - Address: AC:22:0B:32:D3:64
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"ASUS_5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003079abfa26e
                    Extra: Last beacon: 132ms ago
                    IE: Unknown: 0007415355535F3547
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFF0917FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D16990F1600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD090010180202001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 02 - Address: 0E:02:8E:90:AA:B1
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ORBI68"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000029686640627
                    Extra: Last beacon: 4244ms ago
                    IE: Unknown: 00064F5242493638
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B7F
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AAD0903FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1603000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0200000040
                    IE: Unknown: BF0CB2418033FAFF0000FAFF0000
                    IE: Unknown: C005000000FCFF
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010876543219ABCDEF0123408028E90AAB11021000B6F70656E7772742E6F726710230003574150102400033132331042000531323334351054000800060050F204000110110012524253353028576972656C657373204150291008000200001049000600372A000120
          Cell 03 - Address: 12:02:8E:90:68:6C
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000021c27e2183
                    Extra: Last beacon: 4248ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B7F
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0903FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1603000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0200000040
                    IE: Unknown: BF0CB2598933FAFF0000FAFF0000
                    IE: Unknown: C005000000FCFF
                    IE: Unknown: DD1A00904C0408BF0CB2598933FAFF0000FAFF0000C005000000FCFF
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1F8CFDF00000010100000101000000000000FFFF08028E90686F12028E90686C
                    IE: Unknown: DD0B00146C0400000000000000
          Cell 04 - Address: 90:1A:CA:FE:5B:10
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"TG1672G12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d7d8209abf
                    Extra: Last beacon: 4044ms ago
                    IE: Unknown: 0009544731363732473132
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B24
                    IE: Unknown: 2D1AEC0117FFFFFF0000000000000000000000000000001846471100
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500001B127A
                    IE: Unknown: 7F0401000000
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DDA60050F204104A0001101044000102103B00010310470010BC329E001DD811B28601901ACAFE5B101021001A43656C656E6F20436F6D6D756E69636174696F6E2C20496E632E1023001743656C656E6F20576972656C65737320415020322E344710240006434C313830301042000831323334353637381054000800060050F20400011011000B43454C454E4F415032344710080002210C103C0001011049000600372A000120
          Cell 05 - Address: E8:ED:05:56:17:A0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"TG1672GA2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d794e7d13d
                    Extra: Last beacon: 8776ms ago
                    IE: Unknown: 0009544731363732474132
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B24
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 0504000100D4
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601E8ED055617A0103C0001011049000600372A000120
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEC0117FFFFFF0000000000000000000000000000001846471100
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 7F0401000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020061127A
                    IE: Unknown: DD07000C4303000000
          Cell 06 - Address: 90:1A:CA:FE:5B:15
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"TG1672G12-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003d7d8a47859
                    Extra: Last beacon: 3292ms ago
                    IE: Unknown: 000C5447313637324731322D3547
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03012C
                    IE: Unknown: 0706555320240824
                    IE: Unknown: 3C0401162C00
                    IE: Unknown: 2D1AEE0117FFFFFF0001000000000000000000000000001846471100
                    IE: Unknown: 3D162C050400000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010000127A
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320240810
                    IE: Unknown: DDA30050F204104A0001101044000102103B00010310470010BC329E001DD811B28601901ACAFE5B151021001A43656C656E6F20436F6D6D756E69636174696F6E2C20496E632E1023001543656C656E6F20576972656C65737320415020354710240006434C313830301042000831323334353637381054000800060050F20400011011000A43656C656E6F4150354710080002210C103C0001021049000600372A000120
          Cell 07 - Address: 12:02:8E:90:AA:B1
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000029686aa4b6b
                    Extra: Last beacon: 4192ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B7F
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 460573D000000C
                    IE: Unknown: 2D1AAD0903FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1603000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0805000F0200000040
                    IE: Unknown: BF0CB2598933FAFF0000FAFF0000
                    IE: Unknown: C005000000FCFF
                    IE: Unknown: DD1A00904C0408BF0CB2598933FAFF0000FAFF0000C005000000FCFF
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1F8CFDF0000001010001000012028E90686C900008028E90AAB412028E90AAB1
                    IE: Unknown: DD0B00146C0400000000000000
          Cell 08 - Address: DC:3A:5E:DD:2C:99
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000016adda703a
                    Extra: Last beacon: 3996ms ago
                    IE: Unknown: 001600000000000000000000000000000000000000000000
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030108
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021100
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ABC1916FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608001300000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD090010180201004C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD12506F9A09020200272B030600DE3A5EDD2C97
                    IE: Unknown: DD0D506F9A0A00000601111C440096
                    IE: Unknown: DD4D0050F204104A00011010440001021047001022210203040506070809DC3A5EDD2C991049000600372A0001201054000800060050F204000110110011526F6B7520446576696365202D20373935
          Cell 09 - Address: AC:22:0B:32:D3:60
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000038de9030195
                    Extra: Last beacon: 3980ms ago
                    IE: Unknown: 000441535553
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1608081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180209001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00


eno1      Interface doesn't support scanning.


enx001de14bd9fe  Interface doesn't support scanning.
```

---

### Post by tongmengwan on 2018-01-24
I have two wireless access points: 
1(major one). [COLOR=#000000]ESSID:"ASUS_5G", which is 5G. The regular speed in windows will be around 100mbps. but in Linux, it is just about 30
[/COLOR]2  [COLOR=#000000]ESSID:"ASUS", which is 2g. [/COLOR][COLOR=#000000]The regular speed in windows will be 40-50mbps. but in Linux, it is just about 15 [/COLOR]

---

### Post by chili555 on 2018-01-24
We see this:> Cell 09 - Address: AC:22:0B:32:D3:60
Channel:8
Frequency:2.447 GHz (Channel 8)
Quality=55/70 Signal level=-55 dBm 
Encryption key:on
ESSID:"ASUS"Channel 8 is an odd selection since it is also used by another access point in your scan and also because it is not one of the channels that may be selected for the least overlap: [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html)

We suspect, therefore, that your router is set to autoselect the channel. In my experience, Linux drivers and hardware have trouble hopping around continuously. 

If your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Finally, let's be certain you are using the latest firmware; from the terminal:

```
cd /tmp
wget http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.169.1_all.deb
sudo dpkg -i linux*.deb
```After making changes to the router and the computer, reboot both and let us hear if there is any improvement.

---

### Post by tongmengwan on 2018-01-24
I am sorry that the improvement is little. The speed is about 35-40 in Linux. The speed in Windows is about 80. Thus, no obvious improvement. Thank you for kind help.

---

### Post by chili555 on 2018-01-24
Are there any clues in the message log?```
dmesg | grep iwl
```

---

