---
title: "Very little success with Internet"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by ubnubie on 2008-01-29
I was doing great with Ubuntu until the Internet slowed down. I've trawled the site for solutions, but nothing seems to work. I've tried changing DNS numbers, with no luck. Firefox and the Internet connection are working fine under Windows, but under Linux I am just about to give up.

Firefox, Konquerer and Opera all fail in Ubuntu. I've done the www.opendns.com thing, but that has made little difference. The software updates all time out, and so do the Internet pages.

I hate the idea of returning to Windows, but at least that works, and Ubuntu doesn't at the moment (though it did before).

Can anyone help out?

---

### Post by erfahren on 2008-01-29
I don't know a whole lot about this, but some people have mentioned having a problem with ipv6 

I've seen people post different ways of disabling it - I'll just post the links I have and let you look into it (sorry I can't be more specific).
[How-To: Disable IPV6 to speed up Internet](http://ubuntuforums.org/showthread.php?t=87798)
[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)
[http://ubuntuforums.org/showpost.php?p=4225536&postcount=5](http://ubuntuforums.org/showpost.php?p=4225536&postcount=5)

there's also this:
[http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon)

hopefully that will give you something to go on - good luck

---

### Post by Prospero2006 on 2008-01-29
Well, let's try to analyze what's happening on your system. 
if the internet is working on Windows, but not Ubuntu there is a configuration discrepancy 
somewhere. 

So, I'm going to ask you to post the output of a few things:

First:
```

ifconfig

```

then
```

ping www.google.com

```

then
```


ping 216.239.51.104

```

then
```

cat /etc/resolv.conf

```

That should get us started.

Pros
(You post that stuff and I'll provide feedback.)

---

### Post by ubnubie on 2008-01-29
Thanks very much for your help Prospero2006. Sorry for the delay in replying. I got frustrated etc and went to bed! (It was night time here.)

ifconfig produced this:


eth0      Link encap:Ethernet  HWaddr 00:16:D4:A4:DA:4F
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::216:d4ff:fea4:da4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1019 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:680124 (664.1 KB)  TX bytes:130672 (127.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:16:6F:C5:D6:10
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000 Memory:d0000000-d0000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ping [www.google.com](www.google.com) produced this:

PING [www.l.google.com](www.l.google.com) (209.85.173.99) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (209.85.173.99): icmp_seq=1 ttl=240 time=223 ms
64 bytes from [www.google.com](www.google.com) (209.85.173.99): icmp_seq=2 ttl=240 time=225 ms
64 bytes from [www.google.com](www.google.com) (209.85.173.99): icmp_seq=3 ttl=240 time=222 ms
64 bytes from [www.google.com](www.google.com) (209.85.173.99): icmp_seq=4 ttl=240 time=221 ms
64 bytes from [www.google.com](www.google.com) (209.85.173.99): icmp_seq=5 ttl=240 time=221 ms
64 bytes from [www.google.com](www.google.com) (209.85.173.99): icmp_seq=6 ttl=240 time=222 ms
64 bytes from [www.google.com](www.google.com) (209.85.173.99): icmp_seq=7 ttl=240 time=222 ms
64 bytes from [www.google.com](www.google.com) (209.85.173.99): icmp_seq=8 ttl=240 time=223 ms
(It kept going).


ping 216.239.51.104 produced this:

PING 216.239.51.104 (216.239.51.104) 56(84) bytes of data.
64 bytes from 216.239.51.104: icmp_seq=1 ttl=240 time=265 ms
64 bytes from 216.239.51.104: icmp_seq=2 ttl=240 time=263 ms
64 bytes from 216.239.51.104: icmp_seq=3 ttl=240 time=292 ms
64 bytes from 216.239.51.104: icmp_seq=4 ttl=240 time=265 ms
64 bytes from 216.239.51.104: icmp_seq=5 ttl=240 time=263 ms
64 bytes from 216.239.51.104: icmp_seq=6 ttl=240 time=266 ms
64 bytes from 216.239.51.104: icmp_seq=7 ttl=240 time=266 ms
and kept going.


cat /etc/resolve.conf produced this:
search iinet.net.au
nameserver 10.1.1.1
nameserver 28.67.222.22
nameserver 208.67.22.220

---

### Post by ubnubie on 2008-01-29
Thanks very much for your help erfahren. I had to go to bed, so sorry for late reply. This is so frustrating, but I'm trying all those suggestions now, and hopefully something will work!



> **erfahren said:**
> I don't know a whole lot about this, but some people have mentioned having a problem with ipv6 

I've seen people post different ways of disabling it - I'll just post the links I have and let you look into it (sorry I can't be more specific).
[How-To: Disable IPV6 to speed up Internet](http://ubuntuforums.org/showthread.php?t=87798)
[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)
[http://ubuntuforums.org/showpost.php?p=4225536&postcount=5](http://ubuntuforums.org/showpost.php?p=4225536&postcount=5)

there's also this:
[http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon)

hopefully that will give you something to go on - good luck

---

### Post by Iowan on 2008-01-29
No guarantees... but if you're on DHCP, edit /etc/dhcp3/dhclient.conf.  Find/change the line:```
#prepend domain-name-servers 127.0.0.1;
``` to read```
prepend domain-name-servers 28.67.222.22, 208.67.22.220;
```

[This thread]("http://ubuntuforums.org/showthread.php?t=511486") has more details.

---

### Post by ubnubie on 2008-01-29
Thanks again for your help. I disabled the IPV6 thing and it's worked! (I had a bit of a learning curve though, but now I'm a sudo nano flying ace!)



> **erfahren said:**
> I don't know a whole lot about this, but some people have mentioned having a problem with ipv6 

I've seen people post different ways of disabling it - I'll just post the links I have and let you look into it (sorry I can't be more specific).
[How-To: Disable IPV6 to speed up Internet](http://ubuntuforums.org/showthread.php?t=87798)
[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)
[http://ubuntuforums.org/showpost.php?p=4225536&postcount=5](http://ubuntuforums.org/showpost.php?p=4225536&postcount=5)

there's also this:
[http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon)

hopefully that will give you something to go on - good luck

---

### Post by ubnubie on 2008-01-29
Thanks very much for your help -- you guys in here are just great. I disabled the IPV6 thingo, whatever that is, and it's working really fast now, so I don't think I need to do anything else. Thanks anyway.


> **Iowan said:**
> No guarantees... but if you're on DHCP, edit /etc/dhcp3/dhclient.conf.  Find/change the line:```
#prepend domain-name-servers 127.0.0.1;
``` to read```
prepend domain-name-servers 28.67.222.22, 208.67.22.220;
```

[This thread]("http://ubuntuforums.org/showthread.php?t=511486") has more details.

---

