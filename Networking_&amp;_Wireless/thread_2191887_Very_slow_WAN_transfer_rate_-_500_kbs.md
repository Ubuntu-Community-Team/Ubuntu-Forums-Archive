---
title: "Very slow WAN transfer rate - 500 kb/s"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by bphillips2 on 2013-12-04
I am having an issue with really slow transfer rates over WAN between two ubuntu machines.  I am using Bacula to back up my office server at home, it is maxing out at about 500 kb/s transfer rate.  This won't work for what I'm doing.

I have used iperf, this is what I get

> justin@ubuntu:~$ iperf -c xxx.xxx.xx.xxx -p 9102 -i 1------------------------------------------------------------
Client connecting to xxx.xxx.xx.xxx, TCP port 9102
TCP window size: 22.8 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.106 port 45890 connected with xxx.xxx.xx.xxx port 9102
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec   768 KBytes  6.29 Mbits/sec
[  3]  1.0- 2.0 sec   640 KBytes  5.24 Mbits/sec
[  3]  2.0- 3.0 sec   640 KBytes  5.24 Mbits/sec
[  3]  3.0- 4.0 sec   640 KBytes  5.24 Mbits/sec
[  3]  4.0- 5.0 sec   512 KBytes  4.19 Mbits/sec
[  3]  5.0- 6.0 sec   640 KBytes  5.24 Mbits/sec
[  3]  6.0- 7.0 sec   512 KBytes  4.19 Mbits/sec
[  3]  7.0- 8.0 sec   640 KBytes  5.24 Mbits/sec
[  3]  8.0- 9.0 sec   512 KBytes  4.19 Mbits/sec
[  3]  9.0-10.0 sec   640 KBytes  5.24 Mbits/sec
[  3]  0.0-10.4 sec  6.12 MBytes  4.93 Mbits/sec

I have used iperf between two windows machines on the same network (my work computer at the office to my personal computer at home).  These windows machines are at the same locations as my two ubuntu machines and use the same router and network.  They had the same or worse transfer rates.  So I'm pretty sure I can eliminate any hardware or software issues.  I'm sure my problem lies with the routers or my connection.

The client side is on a network with 23 mb/s download and 4.5 mb/s upload
The server side is on a network with 12 mb/s download and .75 mb/s upload

The bacula director is on the server side and directs the client to upload the files to the server.  Therefore I think the files being backed up would be affected by my office 4.5 mb/s upload speed and my home 12 mb/s download speed, correct?

The client side is behind an Asus WL-520GU router running Tomato software, this is bridged with an Actiontec C1000A modem.  The server is hooked into a network switch, but I have bypassed that with no improvement.  Both server and client are hard-wired with cat 5e cables.  The server side is behind a basic actiontec PK5000.  QoS is disabled on both routers.  I tried enabling QoS and set it to give the client machine highest priority and it didn't help. I did not try this on the server side. 

Any idea where to look??

---

