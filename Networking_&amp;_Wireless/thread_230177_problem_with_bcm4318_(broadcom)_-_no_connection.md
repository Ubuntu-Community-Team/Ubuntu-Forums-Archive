---
title: "problem with bcm4318 (broadcom) - no connection"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by hellboy195 on 2006-08-05
hi,
i have read the threads about this problem but it couldn´t help me.
hmm i tried many and many drivers but nothing was usable - to i tried it with ndiswrapper - my laptop is (zv600- printed) - hmm really (zv6100)
```

http://www.ubuntuforums.org/showthread.php?t=197102&highlight=4318 

```

ok the card is aktiv and i configured it but i can´t connect to the internet. (can´t ping the router or [www.google.com](www.google.com) for example)

Some facts:

```
root@ubuntu:~# iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:04:0E:39:22:7E
                    ESSID:"daheim"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-79 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0B:6B:30:33:16
                    ESSID:""
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-94 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

info : The first one is my router , the 2nd a other network in my block of flats - i don´t know who owns it but under winXp it´s no problem

```
root@ubuntu:~# ifconfig eth1
eth1      Protokoll:Ethernet  Hardware Adresse 00:14:A5:2A:09:CF
          inet Adresse:191.168.178.9  Bcast:191.168.255.255  Maske:255.255.0.0
          inet6 Adresse: fe80::214:a5ff:fe2a:9cf/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Speicher:b0204000-b0206000

```

```
root@ubuntu:~# iwconfig eth1
eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx  Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

info: I have konfigured the card mit the gnome-network manger.
I have entered the essid and i tried both : static ip and dhcp.
i also use wep, but under winXp it´s no problem and i tried it also without wep.


i hope anybody could help me - cause i love ubuntu(6.06) ;)

---

### Post by amp_man on 2006-08-05
what driver are you using? bcm43xx or ndiswrapper? if you're using bcm43xx, have you extracted the firmware from the driver? and in either case, can you link to the page you got the driver from? If your laptop is an hp (i think it is) their latest drivers (ver 5.0C) don't work with either driver (ndiswrapper doesn't connect, and bcm43xx-fwcutter can't extract the firmware), you have to use the previous version, 4.0E (i think).

---

### Post by hellboy195 on 2006-08-06
hi,
thanks for your answer.
i have written it : i made it with ndiswrapper.

like this:
```
http://www.ubuntuforums.org/showthread.php?t=197102&highlight=4318 
```

from this side i took that : 
```
http://www.ubuntuforums.org/attachment.php?attachmentid=11584&d=1150897000
```
this is the ndiswrapper with the 5.0c version of the driver.

yes, i have a hp pavilion, BUT i vistited a friend with my laptop and we tried and tried but in the end we made it with ndiswrapper and it was nice.No problem.
Then i went home and tried to make a wlan but i couldn´t connect, but the card is activ.
Now i think the latest drivers (ver 5.0C) must work.Why they worked on my laptop at his home but not in my one? Very Strange

---

### Post by hellboy195 on 2006-08-06
now it runs with wifi-radar :-D 

thx

---

