---
title: "Please help!!"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by sandeepkerala50 on 2011-01-18
Hi
I am sandeep from Kerala, India. I am trying to connect a tata indicom photon whiz to ubundu 9.04 from yesterday. I searched hundreds of pages and made a lot of updates and changes and not fully succeeded. I had spend almost 14 hours to complete all this steps since I am a beginner. Please find my terminal screen shot below and suggest some thing. By  the way the modem is a Huwai EC121.
Thanks in advance

sandeep@sandeep-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CRM=1
AT+CRM=1
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
sandeep@sandeep-desktop:~$ 

Kindly find my conf setings below
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CRM=1
Stupid mode=1
Modem Type = Analog Modem
; Phone = #777
ISDN = 0
; Password = internet
New PPPD = yes
; Username = internet
Modem = /dev/ttyUSB0
Baud = 9600

---

### Post by gordintoronto on 2011-01-18
What is a tata indicom photon whiz?

I suggest using a better message subject, such as "how to use a Tata Indicom printer?" Or whatever it is.

---

### Post by sandeepkerala50 on 2011-01-20
> **gordintoronto said:**
> What is a tata indicom photon whiz?

I suggest using a better message subject, such as "how to use a Tata Indicom printer?" Or whatever it is.
Oh! I am sorry. Tata photon whiz is a wireless modem. The problem still there!

---

