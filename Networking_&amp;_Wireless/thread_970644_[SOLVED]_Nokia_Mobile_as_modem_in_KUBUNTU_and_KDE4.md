---
title: "[SOLVED] Nokia Mobile as modem in KUBUNTU and KDE4.1"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2008-11-04
Afternoon all

I have been connecting to the web via my Nokia 6280 and 6300 successfully for the last year under KDE 3.5 by using the command:

> sudo wvdial

the file /etc/wvdial.conf had been edited to read as follows:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = A
Username = B
Stupid Mode = 1

Now in KUBUNTU 8.1 and KDE 4.1 this does not seem to work any more but knetworkmanager will allow me to create a new connection ttyACM0 when the phone is connected via USB.

Next comes up a "wizard" to set up the connection, see images below.

How do I "translate" what I had before in wvdial.conf into the questions in the "wizard"?

Your help would be greatly appreciated.

---

### Post by AlanR8 on 2008-11-20
Anyone? Can't believe no responses in two weeks!

Come on you experts!!!!!!! :):)

---

### Post by AlanR8 on 2008-11-21
Can't believe it!

Linked up my Nokia today, 6280 and 6300 and with the settings as shown in the original post (pics) they both just worked!

Something must have been updated..........

I'm not in a 3G coverage area today so on the 6280 it's as slow as on the 6300 but I'm posting connected via the 6280 now.

Are there any tweaks that I should make to improve performance?

---

