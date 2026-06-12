---
title: "[SOLVED] Wifi works ... where is the network"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by StageCraft on 2008-02-23
I seem to have been abe too get my wireless card to work on my laptop in Xubuntu but it often wont find any networks when I know that they're there (like the one I'm on now)

anyone know any programs to help find and connect to a wifi hotspot?

---

### Post by Hightide on 2008-02-23
HI StageCraft

Have a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188").It may help

regards

:guitar:

---

### Post by StageCraft on 2008-02-23
no dice. not only can I not use the comand

> colin@colin-laptop:~$ sudo ifconfig eth1 up
SIOCSIFFLAGS: No such file or directory


but when i use iwconfig I get this

> colin@colin-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Encryption key: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

notice the access point. I think that might be the problem

any ideas?

---

### Post by StageCraft on 2008-02-26
Found the problem. I was booting to the wrong kernal half the time and the driver wasn't there. now its all good!:):)

---

