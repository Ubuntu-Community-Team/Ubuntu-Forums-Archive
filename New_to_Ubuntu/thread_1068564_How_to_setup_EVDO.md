---
title: "How to setup EVDO?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-02-13
I am using BSNL-EVDO in India. I am not able to use this 3G wireless device on Ubuntu 8.10. Can u provide me drivers to detect this USB device? Because i have given a lot of try to the techniques given in many linux concerning sites.please rply quick b/c my DSL connection will get cut soon through which i am posting. It's urgent...

---

### Post by ilioscio on 2009-02-13
do you have any more information on the device?

---

### Post by eshant_engineer on 2009-02-13
on running this
```

 wvdialconf /etc/wvdial.conf

```
I m getting this o/p

> Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: QUALCOMM INCORPORATED
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

---

### Post by ilioscio on 2009-02-14
Have you read [[COLOR="Navy"]this[/COLOR]]("http://www.bsnlevdo.com/forums/index.php?showtopic=28") yet? It seems like a pretty good guide.

---

### Post by eshant_engineer on 2009-02-14
ya....definitely, as i told i given a lot of effort.....but by running "lsusb", it is not detecting my USB modem, thus not got o/p Qualcomm, which is displayed when detected.

---

### Post by ilioscio on 2009-02-14
hmmm, can you post your output of lsusb just out of curiosity?

---

### Post by eshant_engineer on 2009-02-14
this the o/p, i m receiving
> Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:fffe  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by golusweet on 2009-02-14
open up your Terminal

sudo gedit /etc/wvdial.conf

Add these lines
[Dialer Defaults]

Modem=/dev/ttyUSB0
Baud=115200
Dial Command = ATDT
Baud=115200
Dial Command = ATDT
init1=ATZ
init2=AT+CRM=1
Flow Control= Hardware (CRTSCTS)
Username = <your username>
Password = <your password>
Phone = #777
Stupid Mode = 1

save it.

type wvdial to connect.

---

### Post by eshant_engineer on 2009-02-15
Thanks....thanks a lot.....one more thing, whenever the ubuntu is restarted, i am required to connect each time by dialing "wvdial".
I tried by adding "wvdial" to session list but not worked. Any sol?

Is there any GUI dialer which i can have to connect, which has txt boxes for username and psswrd?

---

### Post by eshant_engineer on 2009-02-19
but speed is very-very slow than what i get in Vista.........I searched for sol and i got some links:-

1  [http://ubuntuforums.org/showthread.php?t=517591](http://ubuntuforums.org/showthread.php?t=517591)

2 [http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html](http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html)

3 [http://platonic.techfiz.info/2008/04/05/bsnl-ev-do-works-on-hardy/comment-page-1/](http://platonic.techfiz.info/2008/04/05/bsnl-ev-do-works-on-hardy/comment-page-1/)

but what would be the procedure on intrepid.

---

### Post by eshant_engineer on 2009-02-22
Now,i am using intrepid based ultimate ubuntu 2.0.

---

