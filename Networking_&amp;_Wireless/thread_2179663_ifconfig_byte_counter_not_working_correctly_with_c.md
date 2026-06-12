---
title: "ifconfig byte counter not working correctly with curl"
date: 2013-10-09
forum: Networking &amp; Wireless
---

### Post by Ryan_Guthrie on 2013-10-09
I've been banging my head against the wall on this one and desperate for some help.  

I have a computer running ubuntu server 12.04 that has 4 network interfaces.  I'm using curl to download files with the --interface option so that I can download files through different interfaces.  When I check the auth log on the servers I'm downloading from, it shows that I'm coming from the correct IP address depending on which interface I choose.  However, the problem is that the ifconfig byte counters do not register the data on the interface I'm using.  It always adds the bytes to the same interface.  Why is this happening?  For example, when I curl over interface eth2 I want the ifconfig eth2 byte counter to show the traffic but it's showing on interface eth0....

Before....
ifconfig eth0 | grep bytes:           RX bytes:12109794301 (12.1 GB)  TX bytes:137634254 (137.6 MB)
ifconfig eth1 | grep bytes:           RX bytes:2445958906 (2.4 GB)  TX bytes:28105466 (28.1 MB)
ifconfig eth2 | grep bytes:           RX bytes:24355827 (24.3 MB)  TX bytes:7104 (7.1 KB)
ifconfig eth3 | grep bytes:           RX bytes:18755846 (18.7 MB)  TX bytes:7158 (7.1 KB)

curl -o /dev/null --interface eth2 [http://download.thinkbroadband.com/100MB.zip](http://download.thinkbroadband.com/100MB.zip)

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  100M  100  100M    0     0   111M      0 --:--:-- --:--:-- --:--:--  111M

After...
ifconfig eth0 | grep bytes:           RX bytes:12109794301 (12.2 GB)  TX bytes:137634254 (137.6 MB)
ifconfig eth1 | grep bytes:           RX bytes:2445958906 (2.4 GB)  TX bytes:28105466 (28.1 MB)
ifconfig eth2 | grep bytes:           RX bytes:24355827 (24.3 MB)  TX bytes:7104 (7.1 KB)
ifconfig eth3 | grep bytes:           RX bytes:18755846 (18.7 MB)  TX bytes:7158 (7.1 KB)

Here is what my route table looks like...

default via 172.16.0.99 dev eth0  metric 100
172.16.0.0/24 dev eth1  proto kernel  scope link  src 172.16.0.105
172.16.0.0/24 dev eth0  proto kernel  scope link  src 172.16.0.68
172.16.0.0/24 dev eth2  proto kernel  scope link  src 172.16.0.87
172.16.0.0/24 dev eth3  proto kernel  scope link  src 172.16.0.70

I've tried removing the default gateway but that doesn't help.

Help please??

---

### Post by Doug S on 2013-10-09
Hi, and welcome to Ubuntu forums.

I do not think that there was actually a data transfer at all for your example. The before and after byte counts are identical for all interfaces, except for the eth0 bracketed summary which I do not understand.
Also, if I fix up your posted curl output (Note: suggest to use code tags to hold formatting), I get:```
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 100M   100  100M    0     0   111M      0 --:--:-- --:--:-- --:--:--  111M
```meaning it didn't take any time at all. Whereas on one of my 12.04 servers I get:```
doug@doug-64:~/temp1$ ifconfig eth1 | grep bytes
          RX bytes:11963809903 (11.9 GB)  TX bytes:831803195 (831.8 MB)
doug@doug-64:~/temp1$ curl -o /dev/null --interface eth1 http://download.thinkbroadband.com/5MB.zip
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 5120k  100 5120k    0     0   334k      0  0:00:15  0:00:15 --:--:--  366k
doug@doug-64:~/temp1$ ifconfig eth1 | grep bytes
          RX bytes:11969294486 (11.9 GB)  TX bytes:831944202 (831.9 MB)
```which, at least to me, makes more sense. (5484583 RX bytes and 141007 TX bytes (in my case, there would have been other traffic also, in addition to the overhead bytes related to the curl command, accounting for the discrepancy))

---

### Post by Ryan_Guthrie on 2013-10-09
Hi.. thank you.  Sorry I had some copy/paste errors (too many windows open!).

My results actually looked more like what you showed above.  I've been doing lots of web searches and think I narrowed down my issue to the routing tables.  But I'm still not sure how to fix the problem.  Regardless of what interface I define in the curl statement, the traffic always gets added to the eth1 counter.  Also, any traffic that is served up by the box gets added to the same interface regardless of which IP is used.  

Any routing table help for a box with 4 interfaces?

---

### Post by Ryan_Guthrie on 2013-10-11
SOLVED ... this blog was a lifesaver... [http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

---

