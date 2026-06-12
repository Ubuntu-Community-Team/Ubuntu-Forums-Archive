---
title: "Three,co.uk wvdial.conf Settings"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by Mathew1 on 2007-12-10
Hey everyone,

I'm trying to using my Nokia E65 as a modem over bluetooth to access the web on my ubuntu laptop. 
I can get the pairing to work but when I try to run wvdial I get:

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***#1
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***#1
WvDial Modem<*1>: NO CARRIER
WvDial<Warn>: No Carrier!  Trying again.
WvDial<*1>: Sending: ATDT*99***#1
WvDial<*1>: Waiting for carrier.

I believe my wvdial.config file is wrong maybe for this network? My current one contains:
  GNU nano 2.0.6           File: /etc/wvdial.conf                              

[Dialer Defaults]
Modem = /dev/rfcomm0
Phone = *99***#1
Username = ''
Password = ''
New PPPD = yes

Please could anyone help me with this? Thanks

---

