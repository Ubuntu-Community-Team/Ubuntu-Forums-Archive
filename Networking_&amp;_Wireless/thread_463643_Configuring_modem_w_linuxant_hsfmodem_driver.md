---
title: "Configuring modem w/ linuxant hsfmodem driver"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by u238 on 2007-06-03
I'm attempting to switch my laptop (HP zv6000) over to Ubuntu 7.04.  Right now I'm stuck with dial-up, therefore I have to get my modem working.  I ran scanModem and found that I have an ATI SB400 AC'97 Modem Controller and that I need the Linuxant hsf modem driver.  I installed it, and my modem is recognized.  Now I'm stuck at configuring it.  I've tried setting it up by using System > Administration > Network, but I'm clueless as far as actually dialing goes.  I also tried wvdial, following the instructions and substituting my information into the file.  Upon attempting to dial I receive:

ubuntu@ununtu:~$  sudo wvdial
--> WvDial:  Internet dialer version 1.56
--> Initializing modem.
--> Sending:  ATZ
ATZ
OK
--> Sending:  ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuratoin does not specify a valid phone number.
--> Configuratoin does not specify a valid login name.
--> Configuratoin does not specify a valid password.

I'm completely at a dead end, partially because this is essentially my first time ever using Linux of any kind.  Any assistance would be greatly appreciated.  I can post any other information if necessary.

---

### Post by netcrack on 2007-07-19
Press ALT + F2 to open Run Application dialog then type the following command in it

```
sudo gedit /etc/wvdial.conf

```

then type the Phone number, user name, password of u r dial up connection.

save it and try to connect again.

---

