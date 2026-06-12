---
title: "still on RT73 help, please!"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by bianchino on 2008-01-28
:confused:   I have installed the alpha of Kubuntu 8.04. I wish to use my Belkin wireless USB adapter with RT73 so I followed the tutorial found on the internet coming from this forum and called HOWTO: RT73 (RT71) serialmonkey  (Diepruis, April 3rd 3007) and  all the following posts. It goes straight up to a certain point.
I can compile the driver, install everything, but when I type

ifconfig wlan0 up 
 I get
SIOCSIFFLAGS: Invalid argument

here are other attempts:

desktop:~# ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


desktop:~# iwconfig
lo        no wireless extensions.

wlan1     RT73 WLAN
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

I have no other interfaces, no ethernet, no other wireless.
Whato do I have to do, please ? Thanx a lot.:)

---

### Post by yatesy on 2008-01-28
Seems like your interface id is wlan**1** not wlan**0.**
try : ifconfig wlan1 up

---

### Post by bianchino on 2008-01-29
yes of course is wlan1 and I entered ifconfig wlan1 up. wlan0 was simply a typo while submitting the message to the forum. Thanx, anyway!:)

---

### Post by hahahan on 2008-01-29
Bianchino,

Are you root? For getting just a listing from ifconfig or iwconfig you don't need to but for configuring you should use sudo ifconfig or sudo iwconfig.

Just an idea, hopefully helpsome.

Regards.

---

### Post by bianchino on 2008-01-31
yes I'm root!

---

### Post by anidritesolforosa on 2008-02-20
What model is it (your Belkin adapter)? Is it F5D7050B? If yes you might try to install the Windows XP driver after installing ndiswrapper and ndisgtk. Anyway what are you tryong to connect to? From the output of your iwconfig it seems you have not got a router and unless you edited the  HWaddr 00:00:00:00:00:00 line there is something wrong with such Hardware address. Good luck!

---

