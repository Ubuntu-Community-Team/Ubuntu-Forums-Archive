---
title: "how do i install RT3070 driver on my ubuntu 9.10?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by meanfiddler on 2010-02-10
hi,im totaly new to ubuntu. i have an usb wireless air link 25150, and its not working.
 when i follow the troubleshoot guides, i only get to identify that i have a "ID 148f:3070 Ralink Technology, Corp." device. But what now? should i get a driver named rt3070?and how do i install it?

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:55:ee:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1f:1f:55:ee:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
 
IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Managementn
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:110c Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by bkratz on 2010-02-10
Maybe this thread might be of some use to you

[http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070](http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070)

---

### Post by meanfiddler on 2010-02-10
Thank you very very much, its working! he he he he and i could do my self! thank you!:p

---

### Post by bkratz on 2010-02-10
> **meanfiddler said:**
> Thank you very very much, its working! he he he he and i could do my self! thank you!:p

Congratulations!  Please go to the thread tools and mark as [solved} in case it helps someone else..

---

### Post by w2vy on 2010-07-24
Works for Sabrent USB-G802 and on Lucid 10.4

Thanks!

---

### Post by fireoftroy on 2010-09-27
> **bkratz said:**
> Maybe this thread might be of some use to you

[http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070](http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070)

This worked for an AmbiCom WL150N-USBx on 10.04!

This was the simplest solution I've tried and I'm amazed that it finally works (I've been working on this for the past several days)!

---

