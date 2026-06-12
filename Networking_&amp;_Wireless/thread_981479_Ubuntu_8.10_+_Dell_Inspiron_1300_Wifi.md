---
title: "Ubuntu 8.10 + Dell Inspiron 1300 Wifi"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by n1unqn on 2008-11-13
Hi, installed Ubuntu 8.10 running from a windows partition. Everything seems fine except no wifi.

System > Administration > Hardware Drivers = offers nothing (although it did when I used Live CD)

System > Administration > Network = loopback and eth0 (thats what I'm using now to type this so I manages to set that up)

Terminal > iwconfig =

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Any ideas where I've gone wrong? Never setup wifi on linux before. Seems like the Broadcom driver is installed but not talking to Ubuntu?

Thanks :)

---

### Post by n1unqn on 2008-11-13
OK fixed it on my own, here's what I did...

(assuming you have a wired network connection working)

A "Sun" icon appeared on the task bar offering updates

I allowed this

After it finished I rebooted

A "network card" icon appeared on the task bar offering a new driver

I accepted this and activated it

I rebooted again

Now I can see a wifi strength meter in the network icon

I unplugged the network cable and I was told a Wifi connection was found and asked for my WPA password 

Now i have working Wifi on my Dell Inspiron 1300 Whooo!

:biggrin: Maybe solution worth a sticky? The moral is get online and run the updates!

---

### Post by T-RoR on 2009-01-20
Oks, but the connection changes the speed very quickly, 54 Mb/s ... 1 Mb/s ... 11 Mb/s and I must reiniciate the wifi every 2-3 minutes.

Help me please!!

---

### Post by bbr_505 on 2009-01-20
ive got the same problem in ubuntu studio 8.10 with an Intel PRO 4965. however i can't connect by wired either, thus there's no way for me to run the updates and get new drivers etc...

---

### Post by T-RoR on 2009-01-22
Nobody can help me?

---

