---
title: "problem with airtel gprs - nokia modem - ubuntu 7.04"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Ratnadeep on 2008-09-21
hello friends,

I m trying to connect to airtel gprs via nokia 3230 and data cable.
ubuntu - 7.04
After giving the command ' sudo wvdial ', it dials my number from the my phone(seen on phone display)

my wvdial.conf file is as follows -
> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1, "IP","airtelgprs.com"
Modem Type = USB Modem
Phone = 9970266764
ISDN = 0
Password = a
New PPPD = yes
Username = b
Modem = /dev/ttyACM0
Baud = 460800
stupid Mode = 1

and giving the command as ' sudo wvdial ' following message comes -

> rtdp@rtdp-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1, "IP","airtelgprs.com"
AT+CGDCONT=1, "IP","airtelgprs.com"
OK
--> Modem initialized.
--> Sending: ATDT*9970266764#
--> Waiting for carrier.
ATDT9970266764
NO CARRIER
--> No Carrier! Trying again.
--> Sending: ATDT9970266764
--> Waiting for carrier.
[B]ATDT9970266764
NO CARRIER
--> No Carrier! Trying again.
--> Sending: ATDT9970266764
--> Waiting for carrier.[/B]
.
.
.


that bolded part goes on repeating afterwards.

please help me connect it

thanx.:confused:

---

