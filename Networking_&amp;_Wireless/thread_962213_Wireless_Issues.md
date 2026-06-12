---
title: "Wireless Issues"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by jking3826 on 2008-10-29
I've been having lots of issues with my wireless connection.  It seems when I download a new application with the update manager and also browsing a website, my wireless will drop.  And only way I know how to make my wireless work again is restart computer.  The following is output of ifconfig.

wlan0     Link encap:Ethernet  HWaddr 00:XX:05:XX:XX:XX  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3233 errors:4103 dropped:0 overruns:0 frame:0
          TX packets:2341 errors:171 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3582672 (3.4 MB)  TX bytes:263399 (257.2 KB)
          Interrupt:5 Base address:0xa000 

Is it normal to have so many errors?

I'm not sure if I orginally installed the correct drivers as i just tried to make things work. lspci -nn command

00:0a.0 Network controller [0280]: Texas Instruments ACX 100 22Mbps Wireless Interface [104c:8400]

Any help would be appreciated.  Thanks.

---

