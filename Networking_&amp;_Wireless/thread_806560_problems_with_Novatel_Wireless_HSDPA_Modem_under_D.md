---
title: "problems with Novatel Wireless HSDPA Modem under Dell D420"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by trondhuso on 2008-05-25
I have a Dell D420 with an onboard Novatel Wireless HSDPA Modem. This used to work, but I think I messed up things when I tried to use NetworkManager and dial up to connect through the modem.

The modem is recognized through dmesg as ttyUSB0 and ttyUSB1. 

when running wvdial I get this:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
ERROR
--> Bad init string.

the wvdial.conf looks like this:
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = A
Password = B
Stupid Mode = 1

before I do this I do an sudo echo “AT+CPIN=[MY PIN CODE]” > /dev/ttyUSB0 

when running wvdialconf I get this:
$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- ERROR
ttyUSB0<*1>: failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- ERROR
ttyUSB0<*1>: failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- ERROR
ttyUSB0<*1>: and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?

The question "Is it in use by another program" has started me wondering if that is the case. How can I get this information?

Hope for some feedback.
------------------------------
Since this I have found out that this bugs comes because the PUK-code was not written. 
Also found out that after I had used Network Manager, this has saved some settings that tried to start up the modem after every boot. 
So problem is fixed.

---

### Post by trondhuso on 2009-09-24
Well, the problem is not solved.

When running the command wvdialconf wvdialtest.conf

I get the following result:

Editing `wvdialtest.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Speed 9600: AT -- Modem Identifier: ATI -- nothing.
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

I am following the process in tail and when I do, I can see this information:
ATI
Manufacturer: Novatel Wireless Incorporated
Model: Expedite EU870D MiniCard
Revision: 10.9.0102.0-00  [2007-07-03 13:50:21]
IMEI: 355380013492381
+GCAP: +CGSM,+DS

OK
AT
OK
ATI
Manufacturer: Novatel Wireless Incorporated
Model: Expedite EU870D MiniCard
Revision: 10.9.0102.0-00  [2007-07-03 13:50:21]
IMEI: XXXXXXXXXXXXXXX
+GCAP: +CGSM,+DS

OK
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

So when wvdialconf reports that ATI returns nothing, it actually returns 
Manufacturer: Novatel Wireless Incorporated
Model: Expedite EU870D MiniCard
Revision: 10.9.0102.0-00  [2007-07-03 13:50:21]
IMEI: XXXXXXXXXXXXXXX
+GCAP: +CGSM,+DS

Anyone know why this happens?

---

