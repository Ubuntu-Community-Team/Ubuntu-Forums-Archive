---
title: "Problem with GPRS modem setup"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by Mr.nano on 2007-11-14
Hi!

I have GPRS modem(manufactured by Teletonika) but I failed to connect to Internet with it. When typed:

```

desktop:~$ wvdial --config /etc/wvdial.conf gprs
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

```

According to the third line --> Cannot get information for serial port, It seems to me that there might be something wrong with the FTDI driver because I found a Linux manual by Teletonika and it starts with this:

"ModemUSB uses FTDI USB-to-Serial converter. Support for FTDI serial converters was added to Linux kernels from
version 2.6.9 in 2.6 series and from version 2.4.20 in 2.4 series. If driver is compiled as a loadable kernel module, it's
name is ftdi_sio. Most up-to-date distributions should install ftdi_sio module by default."

What I've done since I opened the box is:
Tried to add the following lines and change to what are mine settings to wvdial.conf file as it was written in a document inside the CD that came with the modem:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Username= your login
Password= your password
[Dialer ModemUSB/H1.8]
Carrier Check=no
Check Def Route=on
Dial Command=ATD
Phone =*99#
Init3= AT+CGDCONT=1,"IP","your.apn.here"

and changed them to look like:

 [Dialer Defaults]
Modem = /dev/ttyUSB2
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Username= myname
Password= mypass
[Dialer gprs]
Carrier Check=no
Check Def Route=on
Dial Command=ATD
Phone =*99#
Init3= AT+CGDCONT=1,"IP", internet.vivatel.bg

then I got:

```

desktop:/etc$ wvdial --config /etc/wvdial.conf gprs
--> WvDial: Internet dialer version 1.56
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

```
I didn't find out what was wrong with my Init strings so I've removed wvdial program from Synaptic and install it again 

Then I had premade wvdial.conf file(which seemed that it detected the modem during installation) with the followinf contents:
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>

I changed it to be:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
Phone = *99#
Password = myname
Username = mypass
[Dialer gprs]
Init3= AT+CGDCONT=1,"IP",internet/vivatel.bg

So what should I do?
Any kind of help will be more than appreciated

---

### Post by idsrg on 2008-01-05
Hi,

Were you able to get the problem resolved?

I'm into the same situation. Could you provide with some hints if you are through with it?

My kernel is 2.6.15-29 and I loaded ftdi_sio manually.

Device is detected as ttyATM0

root:~# dmesg | grep tty
[17179593.156000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device

:~# wvdial
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT + CGDCONT = 1, "IP" ,spdns.com
ERROR
--> Bad init string.
--> Cannot get information for serial port.

Please assist. Thanks in advance.

srg.

---

### Post by dishguy123 on 2008-06-20
I'm trying to do the same with Motorola Q & a sony vaio vgn-t370p laptop.  The error I get is :

--> canot open /dev/ttyUSB0: No such file or directory

When I change "USB0" to "USB1 or USB2" respectively, I still get the same error.  Has anyone figured out a way around this?

I just can't get past this....

---

