---
title: "Sierra 881u networks ..."
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by GWBouge on 2008-10-01
As this is my first post, I'll go ahead and give major thanks to everyone that has contributed to this forum, both those with the answers as well as those asking the questions.  This place has been *the* invaluable resource to getting my Ubuntu up and running smoothly.  Ok, now to the point ..

I'm running Ubuntu 8.04 (2.6.24-19) and Vista Home Premium, and have a Sierra 881u aircard (ppp0).  I followed the directions for [installing and connecting]("http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076") with the aircard, and [internet connection sharing]("http://ubuntuforums.org/showthread.php?t=91370"), and everything is working quite well ... with one small annoyance ...

By default, the 881u will connect to whichever of the EDGE(2g) or HSPA(3g) networks it has a better signal to, which is fine I guess for most people, however I live in a very rural area.  Mine *always* defaults to the 2g network.  During the day, trying to get on the 3g network is pretty much useless, given the low signal and high traffic.  Late nights and early mornings, tho, there's little enough traffic to allow me to take advantage of the 3g speeds (even with the poor signal).  On my Vista partition, I use the [Sierra 3g Watcher]("http://www.sierrawireless.com/support/support_and_downloads.aspx?id=4,45,1,1") software (can't stand the at&t connection manager) to connect, in which I can force the card to use the 2g network during the day, and the 3g network at night.

So, finally, all round-about and to the question, is there a program that works on Ubuntu that will let me do this?  Or is there a .conf I can edit to get do the same thing?

---

### Post by arinegara on 2010-05-22
Hi, did you already solve the issue?

Try edit your wvdial.conf as follow:

[Dialer 2G]
Init4 = AT!BAND=04
Init5 = AT!SELRAT=02

[Dialer Defaults]
Modem = /dev/ttyUSB0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","*[YOUR APN]*"
Stupid Mode = 1
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Username = *[your user name]*
Password = *[your password]*
Baud = 9600

[Dialer 3G]
Init4 = AT!BAND=02
Init5 = AT!SELRAT=01

Hope this helps..

---

