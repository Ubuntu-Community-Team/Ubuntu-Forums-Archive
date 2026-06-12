---
title: "wireless problem, i'm going crazy"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by un_polle on 2008-08-15
first: as soon as i had installed ubuntu (a couple of weeks ago) everything worked fine. but after some updates (i think..) the wifi stopped working.

now i've got an intel PRO/Wireless 3945ABG, and i've followed a couple of topic installing this stuff:
>  sudo apt-get install linux-backports-modules-hardy-generic

before that i don't even see the wireless connection in the network menager, now i can see it, but it doesn't find any wireless connection...

if they can help i put down the ouput for ifconfig and iwconfig:

> ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:16:36:3e:3a:f0  
          inet addr:37.240.94.77  Bcast:37.240.95.255  Mask:255.255.248.0
          inet6 addr: fe80::216:36ff:fe3e:3af0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2019 errors:11 dropped:0 overruns:0 frame:0
          TX packets:1600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:11 txqueuelen:1000 
          RX bytes:2604417 (2.4 MB)  TX bytes:169656 (165.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85000 (83.0 KB)  TX bytes:85000 (83.0 KB)

>  iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


p.s.
if i make the hardware testing it gave me the intel PRO/Wireless 3945ABG...so i dont think it's a matter of drivers...but i don't really know causa 'till 2 weeks ago i was on windows....it's my first experience with linux/ubuntu...


sorry for my english :oops:

reading some more topic i've found this one [http://ubuntuforums.org/showthread.php?t=769990]("http://ubuntuforums.org/showthread.php?t=769990")
now i just don't know if that topic can solve my problem (if someone can just say "yes, follow that topic" i'll try) but i've already tried with many ones so before doing another one i wanna check the opinion of someone that knows what's ubuntu  ;)

(also that topic make me wonder if my wireless is up or down...how can i check it? if it's just down i crash my head on a wall)

---

### Post by un_polle on 2008-08-16
up

---

### Post by un_polle on 2008-08-18
pls

---

