---
title: "Internet key mt191up wvdial ppp crash"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by macroman732 on 2014-04-22
Hello, I'm tring connection using internet key ONDA model MT191UP.
But PPP daemon has died.
Can someone help me, please?

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Username = tim
Init1 = ATZ
Password = tim
Modem = /dev/ttyUSB1
Baud = 9600
Init3 =  AT+CGDCONT=1,"ip","ibox.tim.it",,0,0
Stupid Mode = on

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"ip","ibox.tim.it",,0,0
AT+CGDCONT=1,"ip","ibox.tim.it",,0,0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Apr 21 21:54:58 2014
--> Pid of pppd: 2350
--> Using interface ppp0
--> pppd: `&#65533;&#65533; [10]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: `&#65533;&#65533; [10]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: `&#65533;&#65533; [10]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: `&#65533;&#65533; [10]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: `&#65533;&#65533; [10]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> Disconnecting at Mon Apr 21 21:55:29 2014
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

---

