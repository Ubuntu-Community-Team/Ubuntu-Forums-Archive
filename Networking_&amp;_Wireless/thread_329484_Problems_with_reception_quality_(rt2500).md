---
title: "Problems with reception quality (rt2500)"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by bleh on 2007-01-01
Hi all, this isnt really a critical issue, but I thought I'd try and find out if anyone has a solution to the following silly issue I'm encountering.

I use Kubuntu Edgy on my Centrino notebook and it all works perfectly. However, today I decided to try out my rt2500 wireless usb card as well.

It comes up fine, is recognised and so forth. There's just one problem: Reception.

Compared to the built in IPW2200 - reception is dire to non existant. I thought this may be due to the fact that the two cards were possibly conflicting, so I did the obvious and turned the Intel card off - but that didnt improve anything.

I've done other obvious things like stick it into managed mode, double check that it was actually on auto channel etc - and that all seems above board, it's just that the reception plain sucks.

The only reason I'm at all interested in getting the card up and running properly is that I'd like to try using things like airodump-ng/kismet with the rt2500, while I'm on the net with the IPW2200. Basically connecting to a network with the Ralink card doesnt interest me, I dont need to do it - but good reception for passive monitoring is obviously a pre requisit.

Is this in itself possible under Ubuntu, using two wireless cards simultaneously?

One thing to note; I havent been able to do the obvious thing and download drivers from serialmonkey.com because their site appears down today, so I'm still using the default Edgy drivers.

I've found no mention of this poor reception issue anywhere else, so I'm just curious as to whether this is a known problem or whether this is news to people. Or, the other likelyhood - I'm doing something retarded...

There are three quite strong AP's (including my own downstairs) in my immediate area... yet for scan results I get:

```

xxx@xxxx:/usr/bin# iwlist rausb0 scan
rausb0    No scan results

######

xxx@xxxx:/usr/bin# airodump-ng -w xxxx -c 7 rausb0
[CH  7 ][ Elapsed: 3 min ][ 2007-01-01 23:23

 BSSID              PWR  Beacons   # Data  CH  MB  ENC   ESSID
xx:xx:xx:xx:xx:xx   -1        1        0   7  54  WEP? xxxxxxxxxxx

######

xxx@xxxxl:/usr/bin# iwconfig rausb0
rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Frequency=2.442 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-214 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

########

xxx@xxxx:~$ iwlist rausb0 frequency
rausb0    13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.412 GHz (Channel 1)

########

xxx@xxxxl:~$ ifconfig rausb0
rausb0    Link encap:UNSPEC  HWaddr 00-D0-41-F8-0C-98-D0-E3-00-00-00-00-00-00-00-00  
          inet6 addr: fe80::2d0:41ff:fef8:c98/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35190 (34.3 KiB)  TX bytes:53040 (51.7 KiB



```

I'll get at least a few hundred beacons in the space of 3 minutes when using airodump with the Intel card, the fact I only get one or two with the rt2500, is surely indicative of some reception issue?

One point before anyone asks: the card works fine on my XP desktop.

Thanks for reading this rediculously long winded post, and if you have any tips they'll be most appreciated!

---

### Post by trubblemaker on 2007-01-09
I'm in the same situation and you just need to get the correct driver for the card and you need to blacklist the drivers your not using, are you using d-link g122? if so you need to use rt73 driver, and add this to your blacklist:
```
blacklist rt73usb
blacklist rt2500
blacklist rt2570
blacklist RT2500USB

```
if your using another card you'll need another driver, but should still blacklist the ones your not using as the drivers do try to compete

---

