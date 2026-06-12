---
title: "Error 10 wvdial EVDO phone tethering to ubuntu"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by bd1308 on 2008-03-02
I am using wvdial to tether my verizon phoen to ubuntu.

I followed directions, have all of my ducks in a row, and it still doesnt work

i get error 10 when i try:

```
britt@britt-desktop:~$ sudo wvdial
[sudo] password for britt:
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: OK
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: OK
WvDial Modem<*1>: ATDT#777
WvDial<*1>: Fax line detected.  Trying again.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Sun Mar  2 01:21:16 2008
WvDial<Notice>: Pid of pppd: 21503
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: &#65533;*
WvDial<*1>: pppd: &#65533;*
WvDial<*1>: pppd: &#65533;*
WvDial<*1>: Connect time 0.2 minutes.
WvDial<*1>: pppd: &#65533;*
WvDial<*1>: pppd: &#65533;*
WvDial<*1>: pppd: &#65533;*
WvDial<*1>: Disconnecting at Sun Mar  2 01:21:29 2008
WvDial<*1>: The PPP daemon has died: PPP negotiation failed (exit code = 10)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: I guess that's it for now, exiting
WvDial<Notice>: The PPP daemon has died. (exit code = 10)
britt@britt-desktop:~$ 

```

my wvdial.conf file is as follows:
```
[Dialer Defaults]
Stupid Mode = on
Modem = /dev/ttyACM0
Baud = 921600
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#INIT5 = AT+CGDCONT=1,"IP","internet"
Phone = #777
Username = 5025551234@vzw3g.com
Password = vzw
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Auto Reconnect = on
Carrier Check = no
[Dialer shh]
Init3 = ATM0
[Dialer pulse]
Dial Command = ATDP

```

---

### Post by bd1308 on 2008-03-02
If anybody could help me, i would be greatly appreciated

since everybody at work abuses thier internet privelages, I get mine taken away too.....

I'm hoping by using this method, i'm able to at least check my mail......

:rolleyes:

---

