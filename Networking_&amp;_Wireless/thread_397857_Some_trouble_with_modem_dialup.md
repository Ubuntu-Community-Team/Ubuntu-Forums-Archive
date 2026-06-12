---
title: "Some trouble with modem dialup"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by ubuscout on 2007-03-31
Hi people,

finally I've found a pci modem, that maybe could work... after scanmodem utility I get this information

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:09.0	2000:2800	122d:2800	Modem: Smart Link Ltd. Unknown device 2800 

...so after I've found this link 

[http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/)

and i downloaded this package  "slamr-2.6.17-10-generic.tar.gz" 

ps. with uname -r i get this
2.6.17-11-generic    '...just recently updated but I think the package must be good same... ?!?

so after installation e configuration with wdialconf, i try to test it with
"sudo wvdial --config ./wvdial.conf"

but I get this:
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
OK
--> Modem initialized.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187

It seems doesn't get the carrier, I tried also with option "Carrier Check = no" in wvdial.conf but behaviour doesn't change

this is my wvdial.conf :
[Dialer Defaults]
Modem = /dev/ttySL0
Baud = 460800
#Init1 = AT&F
Init1 = ATZ
#Init2 = ATQ0V1E1S0=0&C1&D2X3+FCLASS=0
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
Carrier Check = no
Modem Type = Analog Modem
Phone = 7020187187
New PPPD = yes
ISDN = 0
Username = aaaaa
Password = bbbbb

When I launch "sudo wvdial --config ./wvdial.conf"  I hear clearly the modem get up trying busy the line but nothing more, I don't hear compose number and handshake...

I've tried with pppconfig and after pon "isp"  but do nothing... 

:(

What can I do ? plz for me is important get internet connection with ubuntu...

thanks in advance for your help :)

---

### Post by arsya on 2007-03-31
There are a lot of discussion about softmodem in Linux, and most of them have the similar problem. I am not sure which fault it is, whether the software or the ISP side.
I also have the same NO CARRIER problem. After several attempt, like 10 times, I managed to connect 1 time. Something like that. It's not very convenient, but that's just what happened.

---

### Post by ubuscout on 2007-03-31
<arsya>   ...1 vs. 10 it's just something.... :)  

...for me never... :(   ...anybody have some advice... ?

---

