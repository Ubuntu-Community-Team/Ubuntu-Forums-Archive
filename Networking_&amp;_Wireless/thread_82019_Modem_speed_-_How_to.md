---
title: "Modem speed - How to"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by thinkpadg41 on 2005-10-25
UBUNTU-5.10 and HSF internal modem, Conexant Driver.
======================================================

sudo gedit wvdialconf /etc/wvdial.conf

[Dialer Defaults]
Modem = /dev/modem
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
 Phone = XXX XXXX
 Username = xxxxx	
 Password = xxxxx

 
....to the original wvdial.conf, add "W2" in "Init2 line" and save the file.


Example: 

Init2 = ATQ0 W2 V1 E1 S0=0 &D2 +FCLASS=0



After modification of wvdial.conf, type in terminal:

   sudo wvdial

Now you will see the connection speed.

---

