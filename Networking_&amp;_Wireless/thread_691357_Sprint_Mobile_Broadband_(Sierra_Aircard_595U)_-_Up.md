---
title: "Sprint Mobile Broadband (Sierra Aircard 595U) - Up and running in 5 minutes"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by torgis on 2008-02-08
I am using an Alienware m9700 with a Sierra Wireless Aircard 595U, running Ubuntu 7.10.  I was able to get the mobile broadband working after about 5 minutes of tweaking by doing the following:

# First, set the vendor and product IDs...
sudo modprobe usbserial vendor=0x1199 product=0x0120

# Then, take a look to make sure that your card is now defined
dmesg | grep -i sierra | more

# You should see something like this:
```
ubuntu@ubuntu:~$ dmesg | grep -i sierra | more
[  116.148394] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-s
erial.c: USB Serial support registered for Sierra USB modem (1 port)
[  116.148417] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-s
erial.c: USB Serial support registered for Sierra USB modem (3 port)
[  116.148451] sierra 1-4:1.0: Sierra USB modem (3 port) converter detected
[  116.148749] usb 1-4: Sierra USB modem (3 port) converter now attached to ttyU
SB0
[  116.148859] usb 1-4: Sierra USB modem (3 port) converter now attached to ttyU
SB1
[  116.148970] usb 1-4: Sierra USB modem (3 port) converter now attached to ttyU
SB2
[  116.148976] usbcore: registered new interface driver sierra
[  116.148979] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/sierr
a.c: USB Driver for Sierra Wireless USB modems: v.1.0.6

```

# Then, auto-configure your /etc/wvdial.conf file...
```
ubuntu@ubuntu:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: Sierra Wireless, Inc.
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- OK
ttyUSB0<*1>: Max speed is 460800; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```

# Now, the modem won't connect yet with these settings.  
# You'll need to edit your /etc/wvdial.conf file to match those below:

```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
; Modem Type = Analog Modem
Phone = #777
New PPPD = yes
ISDN = 0
Username = 777
Password = 777
Baud = 460800

```

# Lastly, go to a command prompt and run the dialout proggy...
```
ubuntu@ubuntu:/usr/src$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial<Notice>: Don't know what to do!  Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Fri Feb  8 11:09:37 2008
WvDial<Notice>: Pid of pppd: 9302
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: 0&#65533;[06][08]&#1047;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#1047;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#1047;[06][08]
WvDial<*1>: local  IP address xx.xx.xx.xx
WvDial<*1>: pppd: 0&#65533;[06][08]&#1047;[06][08]
WvDial<*1>: remote IP address xx.xx.xx.xx
WvDial<*1>: pppd: 0&#65533;[06][08]&#1047;[06][08]
WvDial<*1>: primary   DNS address xx.xx.xx.xx
WvDial<*1>: pppd: 0&#65533;[06][08]&#1047;[06][08]
WvDial<*1>: secondary DNS address xx.xx.xx.xx
WvDial<*1>: pppd: 0&#65533;[06][08]&#1047;[06][08]

```

Piece of cake!

Now it's on to this tricky SLI/WINE problem.  I have no trouble running one video card, but the SLI compatibility eludes me still...

Let me know how this works out for you.

Cheers,
-torgis

---

### Post by Wharf Rat on 2008-04-09
Torgis,
Thank you for the post.

However, I have not quite gotten it to work properly.

I have everything on my system and screen that you show except, I am not able to ping or access anything on the internet.  Ip address and DNS server does show up on the screen.

I am using a new Aircard.  Does it have to be activated via Windows as stated in the manual? If so, how under Ubuntu?  

Also, can the script be automated?

---

### Post by torgis on 2008-04-18
I used mine with Windows first so, yes, I would definitely set it up under Windows just to make sure that Sprint has everything working OK on their end.

If the DHCP is assigning you an IP address and auto-configuring your DNS, then we know the connection to their network is ok.  But I am questioning whether or not they are blocking you from going further until you run through their activation and validation routine.

Good luck with this, let me know how it turns out.

-torgis

---

### Post by torgis on 2008-04-18
As to your second question (which I forgot to answer until I read the post again!), yes, it can definitely be automated.

At the most very basic level, you could do something like create a shell script with two lines:

```

#!/bin/bash
nohup wvdial & 

```

chmod it to +x and double-click on it once your system has finished booting.  If you wanted to get fancy, you could set it up so your system automatically dials out when you plug the modem in - but that's beyond the level of what I'm trying to accomplish.  :)  I have a simple icon and it works well for me.

-torgis

---

