---
title: "Xubuntu 14.04.3 x 64 Slow internet connection"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by r102 on 2015-10-07
Hello. Recently my internet connection have slowed down, and I don't figure why. On Windows is working normally. I've installed all updates, and I didn't install any new software

Here are some results for ping 192.168.0.1

64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.509 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.452 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.504 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.493 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.472 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=0.489 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=0.658 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=0.462 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=0.465 ms

And here for ping [www.google.com]("http://www.google.com")

64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=303 ttl=54 time=32.2 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=304 ttl=54 time=33.1 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=305 ttl=54 time=31.6 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=306 ttl=54 time=30.4 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=307 ttl=54 time=30.6 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=308 ttl=54 time=31.1 ms

I don't know if this is relevant, but is the first thing that bumped in my mind

---

### Post by kerry_s on 2015-10-07
that's faster than mine, i'm 60+ ms with a 10% packet loss.

what exactly makes you think it's slow?

---

### Post by r102 on 2015-10-07
I have to wait around 10 seconds to load a webpage. Usually they are loaded very fast, almost instantly. We speak here about the websites that I use frequently. Obviously, some webpages will no load instantly, it depends on the content. But the ones that have heavy content are loaded in 2-3 seconds

---

### Post by r102 on 2015-10-13
I have made a bootable USB with Xubuntu 15.04, I tried it without installing, and the internet works fine on it

---

