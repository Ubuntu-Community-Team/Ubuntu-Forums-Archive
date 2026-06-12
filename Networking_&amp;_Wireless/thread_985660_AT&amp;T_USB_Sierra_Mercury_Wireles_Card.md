---
title: "AT&amp;T USB Sierra Mercury Wireles Card"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by jakrupp on 2008-11-17
I had trouble getting this card to work and found many lengthy posts with doubtful suggestions.  This post

[http://blog.vitriol.net/2008/02/at-wireless-broadband-on-ubuntu-linux.html](http://blog.vitriol.net/2008/02/at-wireless-broadband-on-ubuntu-linux.html)

is quick, easy, and it works.  Here's the wvdial.conf I set up from this.

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Mo
dem Type = USB Modem
baud = 1000000
New PPPD = yes
Modem = /dev/ttyUSB3
ISDN = 0
Phone = *99***1#
Password = CINGULAR1
Username = [email]isp@cingulargprs.com[/email]

ifconfig shows

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:166.217.85.21  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:13718677 (13.7 MB)  TX bytes:1369327 (1.3 MB)


I did need to set up a default route with gw 10.64.64.64, but that could be the result of disabling other interfaces while doing this.

In Greenbelt, MD on a Dell M4400 speedtest.net is reporting 1.2-2Mbps download and up to 300kbps upload.  Hope this helps someone else, because I've wasted two days until I found this simple solution.  This is on 8.10 release.

---

