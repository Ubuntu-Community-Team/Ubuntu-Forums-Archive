---
title: "card can see but have address problem"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by derrylynne on 2006-12-29
My wireless card is seen by ubunti and I can ping, whois etc. I can also use firefox but only if I type the ip address. There is a problem with names - for example I cannot type [www.google.com](www.google.com) as it will just hang. Some info 
IWCONFIG   ra0       RT2500 Wireless  ESSID:"MSHOME"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0F:3D:FD:DA:34
          Bit Rate=54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=62/100  Signal level=-62 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:AC:70:2D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

ra0       Link encap:Ethernet  HWaddr 00:11:50:91:4D:C9
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe91:4dc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:24 txqueuelen:1000
          RX bytes:625322 (610.6 KiB)  TX bytes:223119 (217.8 KiB)
          Interrupt:185 Base address:0x4000

Help very much appreciated

---

### Post by teaker1s on 2006-12-29
seen this several times and the quickest fix is to alter your connection to a static ip address and manually enter your isp DNS ip address in ubuntu.

For some reason certain linux and windows boxes have IPV6 issue-either way manual static ip and DNS will solve it:KS

---

### Post by handy on 2006-12-30
Have a [look here]("http://ubuntuforums.org/showthread.php?t=282034") it may help you out, it can't hurt...

---

