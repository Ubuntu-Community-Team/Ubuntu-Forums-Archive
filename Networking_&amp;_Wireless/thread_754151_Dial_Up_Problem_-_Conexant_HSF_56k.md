---
title: "Dial Up Problem - Conexant HSF 56k"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by Priamo on 2008-04-13
I downloaded Scanmodem
also installed the drivers from the linuxant web
and configured wvdial
and this what comes out

priamo@priamo-laptop:~$ sudo wvdial
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
WvDial<*1>: Sending: ATDT8092203555
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT8092203555
WvDial Modem<*1>: NO DIALTONE
WvDial<Err>: No dial tone.
WvDial<*1>: Disconnecting at Sun Apr 13 13:15:41 2008

Note: It says no dial tone, but im sure my phone has dial tone.


This are my Wvdial configuration

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = 111-111-1111
ISDN = 0
Password = XxXxX  
New PPPD = yes
Username = XxXxX
Modem = /dev/modem
Baud = 115200 

Any help will be unforgivable!!
:KS

---

### Post by Kalawala on 2008-05-21
hey um im having the same problem so im wondering if you found the answer?

---

### Post by wailedhero on 2008-06-07
Hi!

I am also facing problems :( here while configuring the wvdial.conf file. I installed Edubuntu 7.10 on my sister's laptop. Previously she was using Windows XP Pro. But she was unsatisfied from it because of security problems. So I asked her to give linux a try! I  installed edubuntu keeping in mind that it is the most user friendly OS of linux. But believe me! Windows is more user friendly than it!

OK!! Back to my problem!

When I installed Edubuntu 7.10 on my sister's DEL Latitude D600, I had something like this on the panel :

"Restricted Drivers" and blah blah! :lolflag:
What I understood was that my Modem needed some restricted drivers. Then it asked me to install it or not! I continued towards installation. It asked me for the Edubuntu CD. And then after inserting the disk, it finished installing! 

And after that, I kept wandering around in search for creating a dial-up modem connection! :confused:

I clicked on **Network** (System>Administration>Network). I entered all the details in the Modem Properties but unfortunately :( , I found no button or shortcut for connecting! Whats this??!!?!!? :mad:

After searching a lot in ubuntu forums, I knew how to configure the wvdial.conf file. I had configured it like this:

[Dialer Defaults]
Modem = /dev/modem
Modem Type = Analog Modem
Init = ATZ 
#Whats Init & ATZ ? :confused:
Phone = 13177777
ISDN = 0
New PPPD = yes
Username = ptcl
Password = ****
Baud = 115200

But after giving the wvdial command in Terminal, I got this:
```

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem Initiated.
WvDial<*1>: Sending: ATDT13177777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT13177777
WvDial Modem<*1>: NO CARRIER
WvDial Modem<*1>: ERROR
WvDial<Warn>: No Carrier! Trying again.
WvDial<*1>: Sending: ATDT13177777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT13177777
WvDial Modem<*1>: NO CARRIER
WvDial Modem<*1>: ERROR
WvDial<Warn>: No Carrier! Trying again.
**# And it keeps trying to connect.**

```


Pease!!! Will someone give us detailed information for creating a dial-up connection?

My modem is **Conexent D480 MDC V.92 Modem**

Please reply soon so that I could win the bet with my sis, I had bet that Ubuntu is more user friendly than Windows! :lolflag:

---

