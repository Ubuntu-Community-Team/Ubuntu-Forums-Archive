---
title: "Help!! usb720 verizon exit code 2"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by 4wheelin4christ on 2008-01-03
I've googled and read for two days now....

Can someone help me identify the problem??

**********************************************************

wvdial.conf


[Dialer Defaults] 
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 921600
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = [email]asdfasdfsadf@vzw3g.com[/email]
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

***********************************************************

ran as user


matt@matt-desktop:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial Modem<*1>: ATQ0
WvDial Modem<*1>: OK
WvDial<*1>: Re-Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Thu Jan  3 17:07:09 2008
WvDial<Notice>: Pid of pppd: 6251
WvDial<*1>: Disconnecting at Thu Jan  3 17:07:10 2008
WvDial<*1>: The PPP daemon has died: pppd options error (exit code = 2)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: I guess that's it for now, exiting
WvDial<Notice>: The PPP daemon has died. (exit code = 2)
matt@matt-desktop:~$ 


***********************************************************

ran as root

root@matt-desktop:~# wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Thu Jan  3 17:05:56 2008
WvDial<Notice>: Pid of pppd: 6215
WvDial<*1>: Disconnecting at Thu Jan  3 17:05:56 2008
WvDial<*1>: The PPP daemon has died: pppd options error (exit code = 2)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: I guess that's it for now, exiting
WvDial<Notice>: The PPP daemon has died. (exit code = 2)
root@matt-desktop:~# 

***********************************************************

i read the man pppd for exit code 2...but all that suggested was that there is a conflict between two things....


HELP!!!  Thank you to all that suggest anything!

---

### Post by 4wheelin4christ on 2008-01-05
**bump**



Help me obi wan.........

---

### Post by jamesrw on 2008-01-06
I have the same issue, however everything is fine when I run it as root. I did have it working for a while until I reinstalled my distro. I think what I had done in the past is changed the permission on wvdial. give that a try. i have a sprint card, but if it helps, here's my wvdial.conf:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = USB Modem
ISDN = 0
Phone = #777
Modem = /dev/ttyACM0
Username = ''
Carrier Check = no
Password = ''
Baud = 460800
```

---

