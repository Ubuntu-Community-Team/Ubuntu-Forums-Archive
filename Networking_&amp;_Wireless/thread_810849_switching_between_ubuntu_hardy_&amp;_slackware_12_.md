---
title: "switching between ubuntu hardy &amp; slackware 12 stops internet"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by spamhippy on 2008-05-28
well- this is interesting & i'm pretty losted- hoping someone out there can help- here's the story---

my computer is running ubuntu hardy & slackware 12.. my motherboard has a built in lan (Realtek 8201CL PHY) --everything worked great- then one day- internet just stopped. lights flash occasionally on the modem- but no connections.. after several attempts to get it going again- i grabbed a network card that was from a previous computer (a 'network everyone' NC100U-WM) stuck it in the computer & everything worked fine. just recently--the internet stopped working again. & i'm completely losted as to why... additional points of interest...

recently saw an error during start up (uevent no buffer space available) but- after i saw the error- internet was still working.. no problems... but it was the next time i started up after that- that the internet stopped (so *maybe* it has something to do with it..)

both cards (realtek & NC100U-WM) use different driver- realtek is 'forcedeth' & the NC100U is 'tulip'

slackware can still connect to the internet (using either card..) 

there's no windows on this computer... so in short.. i appear to have a network problem that's 

OS related
is not driver related
& possibly the result of switching between linux kernels

any help would be greatly appreciated- thank you...

---

### Post by spamhippy on 2008-05-28
bump!

---

### Post by spamhippy on 2008-05-28
additional information....

eth1      Link encap:Ethernet  HWaddr 00:1a:70:13:a7:11  
          inet6 addr: xxxxxxxxxxxxxxxxxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4580 (4.4 KB)  TX bytes:5940 (5.8 KB)
          Interrupt:5 Base address:0xbc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116900 (114.1 KB)  TX bytes:116900 (114.1 KB)


not good at trouble shooting this stuff- shouldn't i have an inet address for eth1?

SLACKWARE VERSION (which has an inet address..)

eth1      Link encap:Ethernet  HWaddr 00:1A:70:13:A7:11
          inet addr:xx.xx.xxx.xxx  Bcast:xx.xx.xxx.xxx  Mask:xxx.xxx.xxx.x
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:713652 (696.9 KiB)  TX bytes:118269 (115.4 KiB)
          Interrupt:5

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

(to all reading- i crossed out certain information..)

thanks- am confused- any help would be welcomed!

---

### Post by spamhippy on 2008-05-29
bump!

---

### Post by spamhippy on 2008-05-29
wow... anybody out there have any ideas how i can fix this? i'm really stumped over here? please? thanks....

---

### Post by spamhippy on 2008-05-29
i type

ifconfig eth0 xx.xx.xxx.xxx netmask 255.255.240.0 up
ifconfig eth0


setting the inet address- lights blink... no connection.
   
killall networking...
start networking...

still no connection

ifdown eth1
ifup eth1

no connection...

if i mess with this stuff too much & do 'ifconfig' i find that my inet address has disappeared again...

physically turn the dsl off & on a few times- by step & repeat- no connect.. the light occasionally blinks- but no go.

did do all this stuff & after turning the dsl back- started firefox & tried yahoo... got a blank with screen... blinking lights.. but alas- it just hung there & eventually i got the dreaded 'can't connect' 'try again' thing.

why does my inet address keep disappearing?

---

### Post by spamhippy on 2008-05-30
sigh.. still at it.. BOOT!

---

