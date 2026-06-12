---
title: "Can not connect to internet"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by jamil_1 on 2008-03-04
I have a winmodem. I have installed martian. yet i m unable to connect to internet. when ever I try to connect to internet it generates some sort of error some time saying carrier lost or modem hung.
contents of wvdial.config are 

[Dialer Defaults]
Modem = /dev/ttySM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Carrier Check = No

Phone = <Target Phone Number>
Username = <Your Login Name>
Password = <Your Password>



While the error I get is

jamil@jamil-desktop:/etc$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT13177777
--> Waiting for carrier.
ATDT13177777
CONNECT 31200 V42bis
--> Carrier detected. Waiting for prompt.
NO CARRIER
--> Disconnecting at Wed Mar 5 02:35:04 2008

---

### Post by tl3000 on 2008-03-04
> **jamil_1 said:**
> 

Phone = <Target Phone Number>


While the error I get is

--> Sending: ATDT13177777
--> Waiting for carrier.
ATDT13177777


Might want to check the phone number that you're configured to dial--is it correct? is it missing the area code maybe?

---

### Post by dca on 2008-03-04
Winmodems are sketchy at best if they'll work in Linux.  Do you know what type of Winmodem it is?  If you dual-boot w/ Windows and go under the 'device manager' it should reference.
 
I built a system for a friend and threw in a  Lucent modem a while back and used (don't quote me, can't remember) I belive this link to fix...
 
[http://ubuntuforums.org/archive/index.php/t-513395.html](http://ubuntuforums.org/archive/index.php/t-513395.html)
 
...other than that (now) I keep a couple US Robotic external old timey serial modems around just in case because there's no other config needed to connect to internet...

---

### Post by metal_hed on 2008-03-21
at the bottom of the /etc/wvdial.conf file make sure that

Stupid mode = on
Carrier check = no

are there and it should work. worked for me with the same problem.

---

### Post by Eiríkr on 2008-03-21
"Stupid mode = on"???  Is that for real?  <wry dubious grin>

Man, gotta hand it to whoever came up with these config option names.  :o

Cheers,

Eiríkr

---

