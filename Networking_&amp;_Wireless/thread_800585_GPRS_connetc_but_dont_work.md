---
title: "GPRS connetc but dont work"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Digitallad on 2008-05-20
Hi I am a newbie.
Problem: I can connect with my GPRS modem with Wvdial but cant ping a adress or go on the net with firefox.

Here is the connet log:

To run a command as administrator (user "root"), use "sudo <command>".

See "man sudo_root" for details.


paul@paul-desktop:~$ sudo wvdialconf /etc/wvdial.conf

[sudo] password for paul:
Editing `/etc/wvdial.conf'.


Scanning your serial ports for a modem.


ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud

ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud

ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud

ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud

ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Modem Port Scan<*1>: S2   S3   
WvModem<*1>: Cannot get information for serial port.

ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK

ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK

ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK

ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

ttyACM0<*1>: Modem Identifier: ATI -- 144
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


Found an USB modem on /dev/ttyACM0.

Modem configuration written to /etc/wvdial.conf.

ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


paul@paul-desktop:~$ sudo gedit /etc/wvdial.conf

paul@paul-desktop:~$ sudo wvdial gprs

WvDial<*1>: WvDial: Internet dialer version 1.56

WvModem<*1>: Cannot get information for serial port.

WvDial<*1>: Initializing modem.

WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ

WvDial Modem<*1>: OK

WvDial<*1>: Sending: atz

WvDial Modem<*1>: atz

WvDial Modem<*1>: OK

WvDial<*1>: Sending: AT+CGDCONT=1,"IP","internet"

WvDial Modem<*1>: AT+CGDCONT=1,"IP","internet"

WvDial Modem<*1>: OK

WvDial<*1>: Modem initialized.

WvDial<*1>: Sending: ATDT*99***1#

WvDial<*1>: Waiting for carrier.

WvDial Modem<*1>: ATDT*99***1#

WvDial Modem<*1>: CONNECT

WvDial<*1>: Carrier detected.  Starting PPP immediately.

WvDial<Notice>: Starting pppd at Mon May 19 22:06:29 2008

WvDial<Notice>: Pid of pppd: 5994

WvDial<*1>: Using interface ppp0

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]

WvDial<*1>: local  IP address 172.26.121.52

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]

WvDial<*1>: remote IP address 192.168.100.101

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]

WvDial<*1>: primary   DNS address 209.212.97.1

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]

WvDial<*1>: secondary DNS address 10.204.32.245

WvDial<*1>: pppd: h&#65533;[06][08]&#1554;[06][08]


**Here is the WvDial Conf file**


Modem Dialer settings:
[Dialer Defaults]
Init1 = AT+CGDCONT=1,"IP","internet";
Modem Type = USB Modem
Phone = *99***1#
#Phone = *99#
Username = anything
Password = anything
Stupid Mode = 1
Dial Command = ATDT

[dialer gprs]
Modem = /dev/ttyACM0
Baud = 115200
Init2= atz
Init3 = AT+CGDCONT=1,"IP","internet"
isdn = 0
MODEM Type = Analog modem

Hope you can help me!
Paul

---

