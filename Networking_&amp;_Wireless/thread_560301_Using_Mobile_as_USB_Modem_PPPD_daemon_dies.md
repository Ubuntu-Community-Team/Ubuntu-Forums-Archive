---
title: "Using Mobile as USB Modem PPPD daemon dies"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by Michl on 2007-09-26
I followed the directions quoted below adapting it to vodfone here in the Czech Republic (using a Motorola 1200). I connect, but the pppd daemon dies every time after a few seconds. The error code is 16. The /var/log/message is LCP terminated by peer. I have tried adding
Carrier Check = no
Stupid mode = yes
but this does not help.

At home in the US with dial-up I had a similar problem and added S19=0 to the init2 string and that did the trick, but now in the Czech Republic I am using my mobile phone as a USB modem and S19=0 is rejected as a bad string.

In Windows 2000 I have no problems using the phone as a modem (on the same laptop).

Thanks!!!
Michl


> This is intended for Ubuntu 6.06 operated in the UK on the Orange network.

Plug in SE W880i using the USB lead suplied with the phone. There is no need to tell the phone what mode to work in - just leave the mode select message on screen.

Check the USB detection:-
$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0fce:d068 Sony Ericsson Mobile Communications AB
Bus 001 Device 004: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Autodetect the modem using WVDial:-
$ sudo wvdialconf
Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

Edit the .conf file:-
$ sudo gedit /etc/wvdial.conf

It must look like this:-
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","orangeinternet"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99 ***1#
Password = orange
Username = orange

Then launch the connection with:-
$ wvdial

And close the connection with:-
Ctrl^C

---

### Post by Michl on 2007-09-26
Sometimes I wonder why I stick with linux.  Spent several hours going
through /etc/ppp/options playing with the settings.  Nothing works.
So I turn on Windows to use the phone as a USB modem.  No problem
there.  I hate when that happens.

Michl

---

