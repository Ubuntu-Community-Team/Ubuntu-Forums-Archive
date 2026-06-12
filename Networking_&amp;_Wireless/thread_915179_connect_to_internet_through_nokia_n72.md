---
title: "connect to internet through nokia n72"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by krishan008agarwal on 2008-09-09
hi friends i have a problem.
i am not able to connect internet through my mobile in ubuntu.
following is the procedure i have applied, please do let me know where i am going wrong

MOBILE: NOKIA N72
CONNECTION TYPE:USB DATA CABLE
SERVICE PROVIDER: AIRTEL
APPLICATION: MOBILE OFFICE
SERVICE AREA : KOLKATA

WHEN I DIAL IN TERMINAL IT GIVES FOLLOWING OUTPUT:
--> WvDial: Internet dialer version 1.60
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

--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Sun Aug 31 10:30:26 2008
--> Pid of pppd: 3765
--> Using interface ppp0
--> pppd: ........
--> pppd: .........
--> pppd: .......
--> pppd: .........
--> pppd: ............
--> pppd: .........
--> Disconnecting at Sun Aug 31 10:30:33 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ


THIS IS MY WVDIAL.CONIG FILE:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = airtel
Username = airtel
Stupid Mode = 1

I HAVE EDITED "
$ sudo gedit /etc/resolv.conf"
nameserver 202.56.230.5
nameserver 202.56.240.5

ALSO EDITED

$ sudo/sbin/modprobe usbserial vendor = 0x(VID) product = 0x(PID)

WITH MY VENDOR ID AND PRODUCT ID, OBTAINED FROM "$ lsusb" COMMAND

STILL ITS NOT WORKING!
PLEASE HELP ME FRIENDS.......
THANKS!!



also let me know how to connect to internet through wifi. i have compaq pressario c740tu model. WiFi  802.11 a/b/g . please give step by step procedure, as i am still new to ubuntu.

---

