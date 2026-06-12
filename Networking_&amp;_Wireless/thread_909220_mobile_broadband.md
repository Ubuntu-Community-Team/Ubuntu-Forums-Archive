---
title: "mobile broadband"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by billbonza on 2008-09-03
hi. i downloaded ubuntu last night onto an inspiron 1525 running vista home premium.so its now dual boot. it installed with no problems, but i cant connect to the internet.it also doesnt seem to want to read any usb sticks i have plugged in.(apart from the readyboost one)i connect to the net with a three usb modem dongle..mobile broadband(huwaii modem).it recognises all of the devices that are plugged in on the computer section of the ubuntu desktop,but thats as far as i can go. im somewhere between a new and intermediate user, so any explanations that are provided mustnt be too technical.any advice very welcome.thanks.

---

### Post by lunkupe on 2008-09-03
your usb stick works just like a phone modem and therefore it is simple just follow these instructions

ok so here is a document i prepared so just look at it

At this point, I think it's simplest for me to describe what I did to use my mobile phone as a modem.

Before you can do anything, you will need a means to link your phone to your computer, and a copy of wvdial.

To make the connection, if your phone and PC are suitably equipped, you may be able to use Bluetooth or infrared. But my phone, a lowly Nokia 3220, has neither of these. So I used a third-party's USB-Serial data cable, which I believe is a copy of Nokia's DKU-5 cable. Ubuntu identifies it as:

Bus 001 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

Now, connect your phone to your PC, making sure that the phone is on "stand by" (ie not using its WAP browser or making a call). Then give the command

sudo wvdialconf /etc/wvdial.conf

and you should get output along the lines of this:

t0p@lapt0p:~$ sudo wvdialconf
Password:
Usage: wvdialconf <configfile-name>
(create/update a wvdial.conf file automatically)
t0p@lapt0p:~$ sudo wvdialconf /etc/wvdial.conf
Scanning your serial ports for a modem.

Port Scan<*1>: Scanning ttyLTM0 first, /dev/modem is a link to it.
ttyLTM0<*1>: ATQ0 V1 E1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 Z -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyLTM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.31
ttyLTM0<*1>: Speed 4800: AT -- OK
ttyLTM0<*1>: Speed 9600: AT -- OK
ttyLTM0<*1>: Speed 19200: AT -- OK
ttyLTM0<*1>: Speed 38400: AT -- OK
ttyLTM0<*1>: Speed 57600: AT -- OK
ttyLTM0<*1>: Speed 115200: AT -- OK
ttyLTM0<*1>: Max speed is 115200; that should be safe.
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S1 S2 S3 S4 S5 S6 S7 S8
Port Scan<*1>: S9 S10 S11 S12 S13 S14 S15 S16
Port Scan<*1>: S17 S18 S19 S20 S21 S22 S23 S24
Port Scan<*1>: S25 S26 S27 S28 S29 S30 S31 S32
Port Scan<*1>: S33 S34 S35 S36 S37 S38 S39 S40
Port Scan<*1>: S41 S42 S43 S44 S45 S46 S47 S48
Port Scan<*1>: S49 S50 S51 S52 S53
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Nokia
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- ~\uffff
ttyUSB0<*1>: Speed 460800: AT -- [06]\uffff
ttyUSB0<*1>: Speed 460800: AT -- ~\uffff
ttyUSB0<*1>: Max speed is 230400; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyLTM0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ttyLTM0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB0<Info>: Speed 230400; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
t0p@lapt0p:~$

Looking at this output, we can see wvdial found 2 modems: /dev/ttyLTM0 (also known as /dev/modem) and /dev/ttyUSB0. How do we know which (if either) is the phone? By the line:

ttyUSB0<*1>: Modem Identifier: ATI -- Nokia

Wvdial dumps its info to the file /etc/wvdial.conf. If we have a look at that fkile it says:

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
; Username = <Your Login Name>
; Password = <Your Password>

Hmm. Not much good to us, seeing as it's referring to /dev/ttyLTM0, which is my laptop's built-in Lucent winmodem. But wvdial will use this file when dialling out. So we need to edit it. Remember the last 2 lines of all that output from the wvdialconf command? Just kn case your photographic memory's playing up, here they are again:

ttyLTM0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB0<Info>: Speed 230400; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

You'll need to call your cell service provider and get some info from them, such as Username and Password. Then, by amalgamating what you learn from the wvdialconf input and what your friendly cellphone people tell you, you should be able to create an /etc/wvdial.conf file that looks similar to this:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = A
Password = B
Stupid Mode = 1

Your completed file is unlikely to be exactly the same as mine. For instance, for my mobile network (Orange UK) Username and Password are blank. But wvdial doesn't like that, you _must_ put something in there. Also, it will not connect unless you include that line

Stupid Mode = 1

As for that unusual phone number, *99# - that's what you need to make the GPRS connection. Different mobile networks, especially in other countries, will need different numbers. And another user of Orange UK (using a Sony Ericsson phone) reported having to use *99***4*. All I can suggest is: ask your network what to use. If it doesn't work, experiment.

So, now you have a completed wvdial.conf file, and your phone is connected to your computer, all that's left is to try it. Open a console (Ctrl+Alt+F1) and type

sudo wvdial

With any luck, your output will resemble this:

t0p@lapt0p:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Wed Apr 26 23:11:44 2006
--> pid of pppd: 11096
--> Using interface ppp0
--> local IP address 10.33.228.142
--> remote IP address 10.6.6.6
--> primary DNS address 193.35.133.10
--> secondary DNS address 193.35.134.10

Now, the output stops, and seems to "hang". But it's not doing nothing - it's holding the connection open and waiting for you to use it.

To test it, change to another console (eg Ctrl+Alt+F2) and type

ping -c1 80.84.72.25

and if the connection's ok, you should get comething like this:

t0p@lapt0p:~$ ping -c1 80.84.72.25
PING 80.84.72.25 (80.84.72.25) 56(84) bytes of data.
64 bytes from 80.84.72.25: icmp_seq=1 ttl=42 time=781 ms

--- 80.84.72.25 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 781.703/781.703/781.703/0.000 ms
t0p@lapt0p:~$

So, now to do something _useful_ with this internet connection - like surfing the web. Swap to the graphical interface (Ctrl+Alt+F7), and launch Firefox (or whatever browser you have). If you're lucky, it's already configured for this... just type in the URL [www.google.com](www.google.com), and it takes you there!

Note: it very well be quite slow. But that's only to be expected. This isn't broadband, cable, not even 56K dialup. It's a cellular phone, dammit!

Nevertheless, it's very useful. You can web-surf, use telnet and ssh. Downloading software probably isn't a very good idea as it's so slow. Plus a lot of cell plans charge per KB transferred, so you may need to watch your data usage. Then again, if like me you pay a fixed amount no matter how much data you transfer... go for it!!!

When you've finished your session, return to the console where you initiated wvdial (Ctrl+Alt+F1 or whatever) and press Ctrl+C. That will break the connection/hang up.

Well, I can't think of anything to add. If you want to ask me something - feel free!

---

### Post by billbonza on 2008-09-03
thanks for your reply,but im not talking about using my phone as a modem. i connect with a broadband "dongle". the idea being that you can surf anywhere. hsdpa connection through the air.

---

### Post by Jeztastic on 2008-09-04
> your usb stick works just like a phone modem and therefore it is simple just follow these instructions

What he said!!!!

---

### Post by mdbarton on 2008-09-04
I've tried with an EEE (running Xandros) to get online with Three.  It worked till I discovered I was out of covereage!  However, you might find this useful: [http://dalelane.co.uk/blog/?p=254](http://dalelane.co.uk/blog/?p=254) - it's for an EEE, but you should be able to adapt it to a pc/laptop running Ubuntu.

---

### Post by RichmondThuku on 2008-09-07
Thanks Man You saved me from uninstalling UBUNTU YEAH !!! Now i feel one with the world again this time on a Linux kind-of planet.

---

### Post by RichmondThuku on 2008-09-07
[QUOTE=RichmondThuku;5745863]Thanks Man You saved me from uninstalling UBUNTU YEAH !!! Now i feel one with the world again this time on a Linux kind-of planet.And by the way there are some symbols like ';' one MIGHT get right before the Phone Username and Password lines

YOU SHOULD PUT THEM OUT otherwise you'll just go round in circles looking for a solution again and again just like i did.

this one> ; Phone = <Target Phone Number>
this one> ; Username = <Your Login Name>
& this one> ; Password = <Your Password>

Should look like this

Phone = <Target Phone Number>
Username = <Your Login Name>
Password = <Your Password>

:lolflag:

---

