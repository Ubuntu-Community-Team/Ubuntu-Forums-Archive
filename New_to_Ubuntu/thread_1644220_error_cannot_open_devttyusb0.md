---
title: "error: cannot open /dev/ttyusb0"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by alecodd on 2010-12-12
Hi.
I get the following error when connecting thru my wireless modesm w/ the
    `wvdial'
command:

    --> WvDial: Internet dialer version 1.60
    --> Cannot open /dev/ttyUSB0: No such file or directory
    --> Cannot open /dev/ttyUSB0: No such file or directory
    --> Cannot open /dev/ttyUSB0: No such file or directory

my wvdial file is the following:

    [Dialer Defaults]
    Modem = /dev/ttyUSB0
    Baud = 460800
    Init1 = ATZ
    Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
    ISDN = 0
    Modem Type = Analog Modem
    Carrier Check = no
    Dial Command = ATDT
    Phone = *99#
    Username = ppp
    Password = ppp
    Auto Reconnect = yes
    Stupid mode = on

any `lsusb' give the following:
    Bus 005 Device 001: ID 0000:0000
    Bus 004 Device 001: ID 0000:0000
    Bus 003 Device 001: ID 0000:0000
    Bus 002 Device 001: ID 0000:0000
    Bus 001 Device 001: ID 0000:0000


any help, please...

---

