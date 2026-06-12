---
title: "wvdial connected but no internet after sometime"
date: 2016-09-25
forum: Networking &amp; Wireless
---

### Post by bobby24 on 2016-09-25
[COLOR=#242729][FONT=Arial]I have a 3g Dlink Dongle connected to my raspberry Pi running debian based raspbian OS. Initially there is internet available after connecting through evdial. But, after a few hrs, wvdilal is still connected (still has IP address) but there is no internet access. I have to restart wvdial to get connectivity again.
[/FONT][/COLOR]```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 9600
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CFUN 1,0
Stupid Mode = 1
ISDN = 0
Modem Type = Analog Modem
Phone = #777[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Why does this happen ? How to resolve this issue ?[/FONT][/COLOR]

---

