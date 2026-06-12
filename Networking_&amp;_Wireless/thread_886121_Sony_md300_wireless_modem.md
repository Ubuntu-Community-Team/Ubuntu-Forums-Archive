---
title: "Sony md300 wireless modem"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by larreaza on 2008-08-10
I bought this device in order to use internet anywere, but I have to use winxp, because Sony has not support or linux drives for this modem. How to Install in Ubuntu Hardy?

Thanks

---

### Post by canaman on 2008-09-03
I'm tryied a lot. Apears that usbserial wont support it. If someone can help anyway.

> **larreaza said:**
> I bought this device in order to use internet anywere, but I have to use winxp, because Sony has not support or linux drives for this modem. How to Install in Ubuntu Hardy?

Thanks

---

### Post by pclbusto on 2008-09-23
hi I'm from Argetina. sorry if my english isn't good.
the only thing that i coul do with this modem was open a vmware with XP and install the MD300's drivers. With this it's seemms that the modem open others devices inside it and linux could detect others devices. When yo close the vmware the modem shold be flashing if not try installing wirless manager then set the radio alway on ein preference and close de vmware. in linux you shoul see a dev ttyACM0 this is your serial device use wvdial to connect to internet. 
I hope this will help ypu. if you know how to turn on the modem with out vmware please mail me.

---

### Post by canaman on 2008-10-13
Hello people. Actually i can do this modem working!
This is the link, its in Portuguese (is from Brazil, where i live too, because this my English is not so good).

[http://laudecioliveira.org/blog/?p=70](http://laudecioliveira.org/blog/?p=70)

If you cannot understand Portuguese, basically you do this:
- Download this file 
[http://laudecioliveira.org/blog/wp-content/uploads/2008/09/50-md300modem.rules](http://laudecioliveira.org/blog/wp-content/uploads/2008/09/50-md300modem.rules)
- Copy this archive at /etc/udev/rules.d/
- Now edit the wvdial file (i use gnomeppp instead) to math you operator settings - JUST ONE THING, THIS MUST HAVE THE INIT STRING: AT+CFUN=1
See the example /etc/wvdial.conf:
[Dialer Defaults]
Init1 = ATZ
Init2 = AT+CFUN=1
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,&#8221;IP&#8221;,&#8221;bandalarga.claro.com.br&#8221;
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Password = claro
Username = claro

---

