---
title: "can someone make sense of this wvdial output?"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by konstandinos on 2008-08-01
Hi

I am trying to use my Samsung U700 as a modem (connected via USB). I have configured my wvdial.conf and when I execute wvdial at command line I get the following output:

```

WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Fri Aug  1 19:06:48 2008
WvDial<Notice>: Pid of pppd: 8498
WvDial<*1>: Using interface ppp0

```

This waits about a minute and then outputs the following:

```

WvDial<*1>: Disconnecting at Fri Aug  1 19:07:27 2008
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
WvDial<Notice>: Auto Reconnect will be attempted in 80 seconds
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvModem<*1>: Cannot get information for serial port.
...

```

And this just repeats over and over.

Any ideas?

For what it's worth, my vwdial.conf looks as follows:

```

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = user
Password = pass
Stupid Mode = 1

```

I'm not sure what *99# does or the effect of Username and Password. I just followed instructions on a thread in this forum for connecting to the internet through one's mobile.

Thanks.

---

