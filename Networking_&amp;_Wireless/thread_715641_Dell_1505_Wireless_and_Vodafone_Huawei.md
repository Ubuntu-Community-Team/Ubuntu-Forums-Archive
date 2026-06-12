---
title: "Dell 1505 Wireless and Vodafone Huawei"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by sarah.love on 2008-03-05
I've just bought a new Dell computer and decided to move to ubuntu without really knowing too much about it. I'm very keen to use it, but being connected to the internet is apparently vital for this. 

Unfortunately my wireless does not seem to be working: I have a Dell Wireless 1505 Wireless-N Mini-Card - South Africa.

The second thing is that it won't recognise my Huawei E220 USB Modem at all, which means I basically have no internet!!

Please can someone advise [STEP BY STEP - i.e. very new user] on what to do to try and get these things working

Thanks

---

### Post by superprash2003 on 2008-03-05
just to make sure if your wireles card and your USB modem is being detected or not.. open your terminal(Application->accessories->Terminal) and type ifconfig 
 and post results here... just copy  whatever the output is and paste it here

---

### Post by sarah.love on 2008-03-05
sarah@s:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:FE:78:FA  
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fefe:78fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1926897 (1.8 MB)  TX bytes:394297 (385.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


that is what came up.

I've just for the first time realised that my sound is not working either, so it appears that although the system has uploaded, it hasn't really matched itself up with my computer. the only thing that works are USB hard drives and the DVD drive

Appreciate the help. Thanks

---

### Post by superprash2003 on 2008-03-05
from what i can see.. your usb modem should work.. you are getting an IP address 192.168.0.37 from your huawei..
 go to the terminal(applications->accessories->terminal) and type ping google.com and post results here... it could be a DNS issue!!
 about the sound .. try this may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

