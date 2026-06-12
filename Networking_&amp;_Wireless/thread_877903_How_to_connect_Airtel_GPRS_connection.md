---
title: "How to connect Airtel GPRS connection?"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by prakash_dj on 2008-08-02
I tried configuring wvdial.conf with the following,

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
INIT3 = AT+CGDCONT=1,"IP","airtelgprs.com"
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99***1#
Modem = /dev/ttyACM0
Username = airtel
Dial Command = ATDT
Password = airtel
Baud = 115230

getting the following error msg and connection got disconnected after few second..

"The PPP daemon has died: A modem hung up the phone (exit code = 16)"

I got the same error msg in gnome-ppp also. 

Let me know anyone faced the same issue and got resolved ??

---

