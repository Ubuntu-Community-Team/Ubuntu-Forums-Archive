---
title: "Network Manager does not scan for wifi networks but am able to connect via terminal"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by Richik_Jaiswal on 2015-12-17
Hey,

My network manager suddenly stopped scanning for wireless networks but I am able to connect to the wifi using my terminal.
I am using Ubuntu 14.04.3 with Ralink 3290 drivers.

Some commands run that show that I am able to scan through the terminal.
[HR][/HR]
richik@richik-HP-ENVY-TS-15-Notebook-PC:~$ sudo ifconfig wlan0 up
richik@richik-HP-ENVY-TS-15-Notebook-PC:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:1E:A6:02:EE:8C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"whatIsInside?"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005de452716e
                    Extra: Last beacon: 1012ms ago
                    IE: Unknown: 000D776861744973496E736964653F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD8D0050F204104A0001101044000102103B0001031047001000000000000010000000001EA602EE8C1021000B6942616C6C2D4261746F6E1023000A69422D5752583135304E10240003312E3010420003312E301054000800060050F2040001101100203135304D20576972656C6573732D4E20526F757465722069422D575258313530100800020086103C000101


lo        Interface doesn't support scanning.
[HR][/HR]
Also I have tried reinstalling my network manager or restarting it.

PS: I have seen similar threads but none of the solutions proposed are able to solve my issue


Thank you

---

