---
title: "GPRS with QB in Phnom Penh"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by felixdzerzhinsky on 2008-09-26
I am trying to configure my Nokia to work with QB [AKA Cube] in Phnom Penh.

These are their Windoze instructions:

**How to configure dial-up network (direct connection from mobile to PC) ?** 

**For LG handset**

Insert your LG CD driver in to your CD ROM drive. 

[LIST]
[*]Install LG PC Suite in to your computer. After finishing setup, do the following steps 
[*]Connect your USB cable from your PC to LG phone. 
[*]Click on start, programs, LGPC Suite 2, LG PC Suite 
[*]Point to COMMUNICATION then click on internet Kit 
[*]Click on Setting tab then click on New tab 
[*]Type qbmore in the profile box 
[*]Type wap in the APN box 
[*]Type *99***1# in the Call Number box 
[*]Dial-up Number: *99***1#
[/LIST]

How should I do this in Ubuntu?

I am taking a guess (at work as I type this.)

> sudo gedit etc/wvdial.conf

> [Dialer Defaults]
Modem = (your modem)
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99***1#
Username = ""
Password = ""
Stupid Mode = 1

Does the above look correct?

Then??

> sudo wvdial

Or for QB do I need something in the password?

---

### Post by felixdzerzhinsky on 2008-09-26
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","wap"
Modem Type = USB Modem
Phone = *99***1#
Stupid Mode = 1
ISDN = 0
Password = aa
New PPPD = yes
Username = aa
Modem = /dev/ttyACM0
Baud = 460800

I got a hold of a couple QB Technician who use Linux. Apparently a lot of their infrastructure is running on Linux. Fedora no Ubuntu but not Windoze at any rate. :)

---

### Post by Peacepunk on 2009-05-12
Cool, Thanks for sharing, Paul.

Jean-Philippe 'Tropical Ice Cube' Monteiro - in Phnom Penh too...

---

