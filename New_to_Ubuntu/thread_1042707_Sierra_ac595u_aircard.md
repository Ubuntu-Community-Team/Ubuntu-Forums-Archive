---
title: "Sierra ac595u aircard"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by cn5toner on 2009-01-17
hi , i just installed the latest Ubuntu and am totally new to linux. What i am trying to do is setup my Sierra ac595u aircard and have no clue where to start!! Any help would be great.

---

### Post by ieee488 on 2009-01-17
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601)

---

### Post by gstanden on 2010-01-03
Insert the modem into the USB port.  Wait 15 seconds.

Run this command in a terminal:

sudo modprobe usbserial vendor=0x1199 product=0x120

Make sure that your /etc/wvdial.conf file looks like this (after backing up your existing wvdial.conf file first, of course!)

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
; Modem Type = Analog Modem
Phone = #777
Username = 777
Password = 777
ISDN = 0
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyUSB0
Baud = 460800

Now test it by typing in a terminal:

sudo wvdial

You should get output like this:

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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Jan  3 23:54:13 2010
--> Pid of pppd: 5375
--> Using interface ppp0
--> pppd: (up @sp 
--> pppd: (up @sp 
--> pppd: (up @sp 
--> pppd: (up @sp 
--> local  IP address 75.207.114.221
--> pppd: (up @sp 
--> remote IP address 66.174.177.64
--> pppd: (up @sp 
--> primary   DNS address 66.174.95.44
--> pppd: (up @sp 
--> secondary DNS address 69.78.96.14
--> pppd: (up @sp 

(Note that after the message "--> Carrier detected.  Waiting for prompt."
you have to be patient - it will take 15 seconds or so for the rest of the connection to complete)

HTH

---

