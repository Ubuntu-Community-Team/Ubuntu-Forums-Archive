---
title: "Painfully slow SFTP transfers"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by jd6 on 2013-09-19
Ill describe my setup quick. An older server running Ubuntu desktop, connect to a linksys router, then to a power-plug up to my ubuntu box connected to my TV. The only thing my server does is run sickbeard/sabNZB then stream to XBMC.

Lately i've been having alot of problems streaming, its always buffering. If i run a 'iperf" between the two i get...

[U][B]TV as server
[/B][/U]
```
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.7 port 5001 connected with 192.168.1.5 port 43310
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-11.4 sec  4.25 MBytes  3.12 Mbits/sec

```
[U]**Server as Server**
[/U]```
Client connecting to 192.168.1.5, TCP port 5001
TCP window size: 21.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.7 port 43008 connected with 192.168.1.5 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  15.0 MBytes  12.4 Mbits/sec

```

.... so that appears to be fine i suppose, but if i stream through XBMC or Movie player or just copy the file through SFTP i get an average of ~320kb/s so im not sure why the bad transfer rate. I've tried restarting server, TV box, and router multiple times. I will get a decent stream and transfer on occasion though, It's sorta random.

Now i stream through a WD external drive connected through USB and the server hardware is definitely lacking but it streamed 720p at 30fps just fine for a while now and it doesn't seem to make a difference if i copy the media to the internal IDE HDD of the server. And it will stream just fine 75% of time. The TV box could use a ram upgrade (only 1gb) but the only thing open is XBMC so idk if that is a factor or not

I'm just not sure whats going on. I seem to get the same results on my laptop via wireless or wired connection, guess my next step is connect the two straight and try to figure out if it is the server/TV box or the network. It is 1230pm right now and no one is on the network so i should have full bandwidth? ive tried QOS and port priory on the router as well 

Any ideas anyone?

---

### Post by TheFu on 2013-09-19
Being systematic in your testing is needed to figure out exactly where the issue lies.  We need facts, not just "gut feel data".
Make a table with each machine, the type of cables used, the type of NIC on each system, and move the same file (500MB+ in size) back and forth at least 3 times. Measure the clock time for each transfer using "time".  Calculate the throughput.  Do this between every system, switch ports, and over wifi.  BTW, wifi bandwidth is not constant, as you will see. Wifi will never be something you can count on. There are all sorts of ways to interfere with wifi signals.  Use wired if at all possible or learn to live with wifi bandwidth issues.  Getting more than 50% of theoretical wifi bandwidth doesn't happen very often.  Every added device on the wifi network approximately halves the existing bandwidth.

Also be very specific whether it is MB/s or Mb/s.

Also not that different HDDs and disk connection types will have impacts on the throughput.  USB2 sucks compared to USB3 andUSB3 works well until more than 3 different processes try to use the disk.  Nothing can replace the performance of a SATA or eSATA connected drive. Still, the drives cannot keep up with the network after the cache is full. Obviously, SSDs have a better chance of keeping up.

With this data, you'll be able to see patterns and hopefully it is just a bad cable.  OTOH, swapping out a 10/100base-tx network for a GigE network can be done pretty cheaply provided laptops aren't involved.  A GigE 8-port switch is $20 and Intel PRO/1000 NICs are $15-$25 each.  No need to swap the router as devices on the same LAN don't need routing.  Getting 650Mb/s (75MB/s) is fairly routine here.

---

