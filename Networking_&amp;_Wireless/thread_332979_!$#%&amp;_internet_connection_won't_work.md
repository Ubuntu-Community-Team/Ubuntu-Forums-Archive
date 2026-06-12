---
title: "!$#%&amp; internet connection won't work"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by VancouverTT on 2007-01-06
Hi, hope someone can help...

Using Dapper Drake, the third Ubuntu release I've tried and the first that refuses to establish a consistent internet connection (connection still works fine under Windows).

I have a D-Link DSL modem.  My ifconfig looks like this:

---------------------------------
ath0      Link encap:Ethernet  HWaddr 00:11:95:D4:34:57
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fed4:3457/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:297 errors:16521 dropped:0 overruns:0 frame:16521
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:97234 (94.9 KiB)  TX bytes:4987 (4.8 KiB)
          Interrupt:185 Memory:ffffc20000040000-ffffc20000050000

eth0      Link encap:Ethernet  HWaddr 00:11:5B:FD:D7:4B
          inet addr:206.116.214.226  Bcast:206.116.223.255  Mask:255.255.224.0
          inet6 addr: fe80::211:5bff:fefd:d74b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3846 (3.7 KiB)  TX bytes:1320 (1.2 KiB)
          Interrupt:193 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
---------------------------------

I searched some forum threads for help and thought I found a solution when someone suggested removing the line *Acquire::http::Proxy "false";* from /etc/apt/apt.conf.  When I did that, my internet connection started working in firefox and I was able to start downloading Ubuntu updates.  Unfortunately I walked away from my computer while the downloads were happening, and when I returned the screensaver had kicked in and frozen everything.  I had to reboot, and when Ubuntu came back up I no longer had an internet connection.

What's up with that?  I tried *sudo pppoeconf*, but after running for a bit it gave me an error saying something like "We tried to blah blah but couldn't find your blah blah.  Perhaps another blah blah is using your blah blah."

Any suggestions or guesses are appreciated.

---

