---
title: "Huawei E620 problems in 8.04"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by nobbe on 2008-04-30
Hello,
followed some posts of how to get a 3G card to run but all I'm getting is some strange response from my card.

Can you please check my wvdial.conf, if there is anything strange.

# wvdial for 3G card

[Dialer Defaults]

Phone = *99***1#
Username = my SIM card number
Password = my password
Stupid Mode = 1
Dial Command = ATDT

[Dialer huawei_e620]

Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer 3gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",2

[Dialer 384k]

Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

________________________________________________________
Checking for my card with:

lsusb

response:

Bus 006 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

______________________________________________________________

I'm dialing in with:
wvdial huawei_e620 internet 3gonly 384k

response:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.

_______________________________________________________

Is there anybody out there who can help me?
Any help is highly appreciated.

Thanks,
Nobbe

---

