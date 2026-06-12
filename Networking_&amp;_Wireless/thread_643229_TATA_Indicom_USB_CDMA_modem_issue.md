---
title: "TATA Indicom USB CDMA modem issue"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by poision_heart on 2007-12-17
hi i ve sungil SXC-1080 CDMA 1X USB Modem .As i got it from my CDMA mobile service provider tata indicom in india...I am trying to connect it on gutsy...ubuntu detected modem very well ..i tried to config it  using wvdialconfig everything is going well but when i am running wvdial R for connectiing to internet it showing me eror in username or password or phone number.i already edited those details in wvdial.conf.but still i am unable to connect internet..service provider also given same procedure to work sungil CDMA modem in linux...pls help me to connect it

for ref i m posting here my wvdial.conf and error message

my wvdial.conf is

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
; Phone =#777
ISDN = 0
; Password =internet
New PPPD = yes
; Username =internet
Modem = /dev/ttyACM0
Baud = 460800

and error after wvdial R i m getting is -

praveen@x-zone:~$ sudo wvdial R
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Warn>: Warning: section [Dialer R] does not exist in wvdial.conf.
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<Err>: Configuration does not specify a valid phone number.
WvDial<Err>: Configuration does not specify a valid login name.
WvDial<Err>: Configuration does not specify a valid password.
praveen@x-zone:~$ 


pls guide me whats wrong..

regards

---

### Post by poision_heart on 2007-12-25
hi friends

Merry Christmas to you all!! well on christmas eve i got success in connecting internet on mint finally using my CDMA modem i just wanna share my script with u guys so that u all can connect net from CDMA usb medem

here is my new wvdial.conf


[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
+FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = #777
Username = internet
Password = internet
stupid mode = 1

this is my working script..enjoy

thanks

---

### Post by jackiethegreat on 2007-12-25
Hello

I Have Changed My Config File With Your Settings, But I M Not Able To Connect To Internet Instead. The Error Is That When I Click Connect Button, It Starts Connecting To Internet And Hangs On Sending Password Message ....i Waited For 30 Minutes But No Connection Has Been Made. Please Tell The Whole Procedure To Connect To Internet Using This Usb Tata Indicom Modem, I Will Be Grateful To You.

Please Help Me Me... I M Waiting For The Reply.



Regards,
Jackiethegreat

---

