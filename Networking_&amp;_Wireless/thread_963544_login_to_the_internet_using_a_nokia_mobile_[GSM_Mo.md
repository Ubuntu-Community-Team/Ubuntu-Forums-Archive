---
title: "login to the internet using a nokia mobile [GSM Modem]"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by kmk4 on 2008-10-30
[B][COLOR="Blue"]hi everyone 
i was using my Nokia N80 to log into internet in WindowsXP using Nokia PC suite for a long time
i'm trying to use the same mobile with ubuntu to login internet 
i did the following[/COLOR][/B]
from terminal i loged as root then

**[COLOR="Red"]lsusb[/COLOR]**
i found my phone like the following
[COLOR="Blue"]Bus 007 Device 004: ID 0421:0445 Nokia Mobile Phones[/COLOR]


then i typed 

[COLOR="Red"]  /sbin/modprobe usbserial vendor=0x421 product=0x445[/COLOR]
nothing returned then i typed

[COLOR="Red"]wvdialconf create[/COLOR]
it gives me the following results
[COLOR="Blue"]
Editing `create'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3  
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- Nokia
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found an USB modem on /dev/ttyACM0.
create<Warn>: Can't open 'create' for reading: No such file or directory
create<Warn>: ...starting with blank configuration.
Modem configuration written to create.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
[/COLOR]

then i update the wvdial file like following i typed

[COLOR="Red"]gedit /etc/wvdial.conf[/COLOR]
the file content is 

[D[COLOR="Blue"]ialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = internet
Password = internet
Stupid Mode = 1
[/COLOR]

then i launch wvdial

[COLOR="Red"]wvdial[/COLOR]

i get the following result
[COLOR="Blue"]
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Oct 30 16:17:37 2008
--> Pid of pppd: 6715
--> Using interface ppp0
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> Disconnecting at Thu Oct 30 16:17:41 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Oct 30 16:17:49 2008
--> Pid of pppd: 6749
--> Using interface ppp0
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> pppd: h&#65533;[06][08]
--> Disconnecting at Thu Oct 30 16:17:53 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
[/COLOR]

[COLOR="Green"][SIZE="4"]the modem is disconnected again and again
i can't access the internet 
i made everything right as i found in the forum but i still can't access internet help me please[/SIZE][/COLOR]

---

### Post by mishivia on 2008-10-30
Hi, can you tell me how you were able to detect your phone as a modem? Do you have a usb or a bluetooth dongle? I have both a sez310a and a nokia using a bluetooth dongle and still no success.

---

### Post by kmk4 on 2008-10-31
just follow the steps i made it suppose to connect it via usb cablei'm connecting my phone via usb cable
and it takes the followimg port
/dev/ttyACM0  which is the port of virtual com port for usb
to make sure from the port i do the following
in the shell i typed the following
#screen /dev/ttyAM0 
this will open a terminal with your phone type
ATDT999
your phone will dail 999
then the port is ok
but the problem that i made everything 
but something is missing that i can't tell
that prevent me from getting connected to he internet via my phone

---

### Post by kmk4 on 2008-10-31
no one knows how to fix this ?

---

### Post by mishivia on 2008-11-14
Hi. Did you ever solve your problem?

---

### Post by GoodPanos on 2008-11-14
I don't know if this helps but if you are using Intrepid Ibex (8.10) it should work automatically.

Just plug in your phone via USB, select PC Suite on the phone, and NetworkManager should pop up a message saying a wireless connection is found (something like that).  Then it goes through a wizard where you select your country and carrier and then click on connect and you are on :guitar:

In my situation I had to plug my phone in twice but after that it worked like a charm and still does.  BTW I have a Nokia E61i with T-Mobile USA.

---

### Post by mishivia on 2008-11-16
well, I will wait for intrepid to come in the mail then or this IT guy in my family recommended freesbd or something like that. 
thank you, though.

---

