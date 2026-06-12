---
title: "Server losing pppoe connection?"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by marko-manchev on 2014-08-28
**Hello,**
**From a couple of days ago, I am experiencing strange behavior with by Ubuntu Server box.**
[B]
I have it conf as a gateway, with two nics and a pppoe connection to ISP. [/B]
[B]
Everything works fine, until i get this msg in syslog:[/B]



[LIST]
[*] Aug 28 22:07:45 gateway pppd[1028]: No response to 4 echo-requests
[*] Aug 28 22:07:45 gateway pppd[1028]: Serial link appears to be disconnected.
[*] Aug 28 22:07:45 gateway pppd[1028]: Connect time 188.1 minutes.
[*] Aug 28 22:07:45 gateway pppd[1028]: Sent 53583837 bytes, received 34345122 bytes.
[*] Aug 28 22:07:51 gateway pppd[1028]: Connection terminated.
[*] Aug 28 22:07:51 gateway pppd[1028]: Modem hangup
[*] Aug 28 22:08:56 gateway pppd[1028]: Timeout waiting for PADO packets
[*] Aug 28 22:08:56 gateway pppd[1028]: Unable to complete PPPoEDiscovery
[/LIST]


****Ifconfig clearly shows that I have lost the ppp interface:****


 - eth0      Link encap:Ethernet  HWaddr 6c:62:6d:ad:61:ff


          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:736900 (736.9 KB)  TX bytes:3048256 (3.0 MB)


 - eth1      Link encap:Ethernet  HWaddr 00:e0:52:fa:22:13


          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:42 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


 - lo        Link encap:Local Loopback


          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10649 (10.6 KB)  TX bytes:10649 (10.6 KB)


**pon/poff doesn't help.

And the strange thing is:** when i do a FULL POWER CYCLE (shutdown -P now, then manually starting the PC), everything is back to normal. PPP is there**, until it hangs up again!
When i do a shutdown -r now, init 6 or reboot, PPP is not there.
Thanks upfront.**

---

