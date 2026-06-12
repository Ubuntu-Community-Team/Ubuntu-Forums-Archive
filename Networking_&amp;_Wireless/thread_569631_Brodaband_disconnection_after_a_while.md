---
title: "Brodaband disconnection after a while"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by amitabhishek on 2007-10-07
Hi,

I use Ubuntu 7.04 and have a broadband internet connection through a ethernet card. I always get disconnected after say half an hour of happy browisng. I have to relogin again & again. What could be the reason? How do I cure it? Even in Suse I had the same problem.It doesn't happen in XP. I have pinged and the Ubuntu vs. XP output are pasted below. Pls help!

amit@amit-desktop:~/Desktop$ 


amit@amit-desktop:~$ ping -c 4 google.com

PING google.com (72.14.207.99) 56(84) bytes of data.

64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=230 time=391 ms

64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=230 time=395 ms

64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=4 ttl=230 time=390 ms



--- google.com ping statistics ---

4 packets transmitted, 3 received, 25% packet loss, time 3005ms

rtt min/avg/max/mdev = 390.079/392.260/395.059/2.079 ms

amit@amit-desktop:~$ 


Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.


C:\Documents and Settings\Amit Abhishek>ping -n 4 google.com

Pinging google.com [72.14.207.99] with 32 bytes of data:

Reply from 72.14.207.99: bytes=32 time=398ms TTL=230
Reply from 72.14.207.99: bytes=32 time=390ms TTL=230
Reply from 72.14.207.99: bytes=32 time=389ms TTL=230
Reply from 72.14.207.99: bytes=32 time=382ms TTL=230

Ping statistics for 72.14.207.99:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 382ms, Maximum = 398ms, Average = 389ms

Rgds,

---

### Post by aashay on 2007-10-07
i would advise you to get rid of sify... it probably has to do with their silly dialer thingies (heartbeat, keep-alive and what now)

---

