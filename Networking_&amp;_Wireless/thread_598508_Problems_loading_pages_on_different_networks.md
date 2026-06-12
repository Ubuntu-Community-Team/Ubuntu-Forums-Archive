---
title: "Problems loading pages on different networks"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by alexoz on 2007-10-31
Hello everyone
Kind of new to Linux, but had used Ubuntu since 5.04 and have never ran into this problem.

I am currently running Gutsy 7.10 on a Gateway laptop and everything good so far, however when I connect to an ADSL connection, pages take forever to load, I have also connected to some other hot spots here in town with the same results, But, if I connect at work's LAN, it's like night and day difference.
I know the LAN at work is fast, however, the difference is really noticeable.

I have not changed anything as far as the config goes (DNS, or anything like that)
Any ideas on what to check for?

Thanks

---

### Post by jonobr on 2007-10-31
You need to do some ping/ latency/traceroute testing to see what your connections are like in those locations.

It sounds as if your network is set up just fine to connect to each of these hotspots, just your performeance sucks everywhere expect work.
Go to  system ->adminsitration -> network tools 

You can use ping to show what response times are like.

Select your network device in Devices tab , and in ping, put in an address like pingplotter.com, see what you get back.

Use the same test for your different hotspots.
It should show marked difference in your location..

Im assuming your using the same device in all locations

Thanks

PS you can use ping on the command line without using the gui

---

### Post by alexoz on 2007-10-31
Here's what I got on both connections (using LAN connection, not wireless)

First connection is the LAN here at work
the second one is a test adsl connection at work too, but it's an outside line (adsl) same dns though

on the adsl connection, resolving seens to be taking forever, a friend here suggested to use opendns, but didnt see a difference.
Didnt think it was a MTU issue on the adsl modem, and the fact that it acts the same on some other networks puzzles me

alex@alex-laptop:~$ ping [www.pinglotter.com](www.pinglotter.com)    ----------THIS IS THE ADSL
PING [www.pinglotter.com](www.pinglotter.com) (66.45.254.244) 56(84) bytes of data.
64 bytes from 66.45.254.244: icmp_seq=1 ttl=49 time=51.6 ms
64 bytes from 66.45.254.244: icmp_seq=2 ttl=49 time=51.3 ms
64 bytes from 66.45.254.244: icmp_seq=3 ttl=49 time=53.6 ms
64 bytes from 66.45.254.244: icmp_seq=4 ttl=49 time=64.1 ms
64 bytes from 66.45.254.244: icmp_seq=5 ttl=49 time=50.1 ms
64 bytes from 66.45.254.244: icmp_seq=6 ttl=49 time=50.8 ms
64 bytes from 66.45.254.244: icmp_seq=7 ttl=49 time=51.0 ms
64 bytes from 66.45.254.244: icmp_seq=8 ttl=49 time=49.1 ms

--- [www.pinglotter.com](www.pinglotter.com) ping statistics ---     ------------THIS IS WORK's LAN
8 packets transmitted, 8 received, 0% packet loss, time 40525ms
rtt min/avg/max/mdev = 49.137/52.752/64.153/4.481 ms
alex@alex-laptop:~$ ping [www.pinglotter.com](www.pinglotter.com)
PING [www.pinglotter.com](www.pinglotter.com) (66.45.254.245) 56(84) bytes of data.
64 bytes from 66.45.254.245: icmp_seq=1 ttl=49 time=64.2 ms
64 bytes from 66.45.254.245: icmp_seq=2 ttl=49 time=61.1 ms
64 bytes from 66.45.254.245: icmp_seq=3 ttl=49 time=64.4 ms
64 bytes from 66.45.254.245: icmp_seq=4 ttl=49 time=63.5 ms
64 bytes from 66.45.254.245: icmp_seq=5 ttl=49 time=65.2 ms
64 bytes from 66.45.254.245: icmp_seq=6 ttl=49 time=62.0 ms

--- [www.pinglotter.com](www.pinglotter.com) ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 25398ms
rtt min/avg/max/mdev = 61.114/63.436/65.256/1.450 ms

---

