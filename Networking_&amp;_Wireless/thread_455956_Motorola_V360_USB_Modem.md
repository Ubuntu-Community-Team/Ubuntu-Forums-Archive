---
title: "Motorola V360 USB Modem"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by Hark3n on 2007-05-27
Hi,

My wife recently got a Motorola V360 cellphone.  At home we currently use my cellphone as a 3G modem.  This is a problem for when I'm away, as she cannot access the net from her phone on linux.

I have tried setting the phone up for bluetooth connection, but the connection just gets dropped.

I have also tried this link: [http://ubuntuforums.org/showthread.php?t=109950](http://ubuntuforums.org/showthread.php?t=109950), but that only returns /usr/sbin/pppd: unknown host: -connect

Finally I've tried to get it to work through kppp.  After fiddling with the modem settings I finally got it to dail, but got the following in the log :

ATZ
OK
ATM1L1
OK
ATDT*99*#
ERROR

If there is anyone that knows how I could solve this problem, please post.

Thanks,
E

---

### Post by Robertk on 2008-03-31
Hi, I also have a V360, and after struggling for a long time to connect, I found a wonderful tool, GPRS Easy Connect.

GPRSEC makes connecting to the net using a mobile phone very easy. It supports many different phones and many different networks.

I use it all the time on my V360, however I use it with the USB cable, not bluetooth, so I'm not sure if it will work. But give it a try anyways.

The last time I checked, there were no packages for it, however you can download it from [http://gprsec.linuxforum.hu/](http://gprsec.linuxforum.hu/) and it has a graphical installer to make things easy(ish).

Good luck

---

