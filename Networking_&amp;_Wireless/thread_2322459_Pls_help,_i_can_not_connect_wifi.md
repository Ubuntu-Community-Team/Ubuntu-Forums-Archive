---
title: "Pls help, i can not connect wifi"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by ARKADIY_MISHIN on 2016-04-28
hi, i have system "ubuntu 16:04"
Linux arkadiy-Lenovo-YOGA-Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Have wifi adapter:
01:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)

i install driver from 
[https://github.com/kvalo/ath10k-firmware/tree/master/QCA9377/hw1.0](https://github.com/kvalo/ath10k-firmware/tree/master/QCA9377/hw1.0)

and i have two wifi AP

```
[COLOR=#000000][FONT=dejavu sans mono]          Cell 08 - Address: 00:25:9C:6E:7A:2B[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Channel:5[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Frequency:2.432 GHz (Channel 5)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Quality=70/70  Signal level=-26 dBm[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    ESSID:"arkasha18_2"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                              36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Extra:tsf=000000000221db91[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Extra: Last beacon: 3280ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 000B61726B6173686131385F32[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 010482848B96[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 030105[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 0406000100000000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 2A0100[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 32088C129824B048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                        Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                        Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                        Authentication Suites (1) : PSK[/FONT][/COLOR]

```

and second

```
[COLOR=#000000][FONT=dejavu sans mono]         Cell 10 - Address: F0:25:B7:8F:3F:1F[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Channel:6[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Frequency:2.437 GHz (Channel 6)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Quality=70/70  Signal level=-39 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    ESSID:"SamsungAr"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Extra:tsf=00000000016db31a[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    Extra: Last beacon: 3448ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 000953616D73756E674172[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 010882848B962430486C[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 030106[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 2A0100[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 2F0100[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                        Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                        Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                        Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 32040C121860[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 2D1A2D1117FF00000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 3D1606080000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: 7F080400008001000040[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: DD050016328000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: DD090010180200001C0000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                    IE: Unknown: DD1E00904C0408BF0C32018003FEFF0000FEFF0000C0050006000000C3020010[/FONT][/COLOR]

```


i can connect with "SamsungAr"(phone Samsung note3) but can not connect with "arkasha18_2"(router linksys wrp400)

why? i not understend
i try make same password. same AP name and same authorization, but not work.

syslog > QCA9377 Reason: 2=PREV_AUTH_NOT_VALID

debug wpa_supplicant 
[http://inmob.de/down/asdasd.txt](http://inmob.de/down/asdasd.txt) - can not connect (linksys wrp400)
[http://inmob.de/down/asdasd1.txt](http://inmob.de/down/asdasd1.txt) - can connect (Samsung note3)

From windows10 on this laptop i can connect and Samsung  and linksys
if i off authorization om linksys, all ok, wep/wpa/wpa2 - can not conenct.
I tried to change channels(same Samsung[COLOR=#000000][FONT=dejavu sans mono]:2.437 GHz (Channel 6)[/FONT][/COLOR] ) not help .

pls help

thx

---

### Post by ARKADIY_MISHIN on 2016-05-06
somebody, any ideas?

---

### Post by ARKADIY_MISHIN on 2016-05-10
i buy new AP 'NanoStation M2' and all ok.

---

