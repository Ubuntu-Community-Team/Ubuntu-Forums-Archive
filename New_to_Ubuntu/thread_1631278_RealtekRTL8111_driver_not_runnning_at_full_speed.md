---
title: "RealtekRTL8111 driver? not runnning at full speed"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by powel212 on 2010-11-26
I have GA-P43T-UD3L with RealtekRTL8111 but can't get it over 54MB/s

The built in ubuntu driver seems to be choked.

Is there a better driver for this chip?

On Mac and windows I can get the same chip to run over 100MB/s

I have checked the cabling and have run iperf but can't seem to figure out the choke.

I tried downloading the driver from realtek.com but it is FTP only. arg. I even called Realtek in Taiwan but they seem like they have no idea what they are doing.

Any help is appreciated.

Powel

---

### Post by MooPi on 2010-11-26
I just downloaded from Realtek :
[http://dl.dropbox.com/u/5209151/r8168-8.020.00.tar.bz2]("http://dl.dropbox.com/u/5209151/r8168-8.020.00.tar.bz2")
Good instruction in the readme file
What kernel are you running, I just noticed Jaunty in your signature ?
```
uname -r
```

---

### Post by powel212 on 2010-11-26
Thanks a lot.

I am running 10.10 just haven't changed my sig for a long time.

I'll give it a try.

Do you know what driver is default on 10.10? It seems slow.

Powel

---

### Post by powel212 on 2010-11-26
By using the driver you posted, following the instructions and forcing link status I was able to get it up to:
```
$ iperf -c 192.168.0.50
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.43 port 59908 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.02 GBytes    878 Mbits/sec
```

I can't cry about that.

I tried assigning mtu 6000 but I am not sure I did that correctly. The readme was not really clear on this point. 

I can live with it the way it is now. Though I might play with it some more to get it up to full capacity.

If anyone has any suggestions about how to accomplish that I would appreciate the feedback.

Thanks for your help.

Powel

---

