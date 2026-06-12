---
title: "Wvdial connect to usb modem problem"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by craffojf on 2008-01-29
This is my wvdial.conf file

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = password
Username = john

This is the output I get.

john@john-desktop:~$ wvdial
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
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial<Err>: Connected, but carrier signal lost!  Retrying...
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~~[7f]}#@!}!2} }2}"}&} } } } }#}$@#}'}"}(}"o=~
WvDial<Warn>: Timed out while dialing.  Trying again.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: 0
WvDial Modem<*1>: 0
WvDial Modem<*1>: 0
WvDial<Warn>: Timed out while dialing.  Trying again.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: 0
WvDial Modem<*1>: 0
WvDial Modem<*1>: 0

If anybody can help me with this or if there is a better way, please let me know.

Thanks

---

