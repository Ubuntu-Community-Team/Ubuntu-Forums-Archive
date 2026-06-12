---
title: "[Ubuntu] apt update hanging : IPV6"
date: 2014-07-14
forum: Networking &amp; Wireless
---

### Post by ashley8 on 2014-07-14
Hi,

So when I run "apt-get update"  or try to install any package the first time each day it hangs for about 5 mins on...
 
```
sudo apt-get update
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::19)] [Connecting to s
```

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty



Thanks!

---

### Post by bapoumba on 2014-07-14
Does it finally update ? How are you connected to the internet ?

---

### Post by ashley8 on 2014-07-14
Yes it eventually works
I'm connected with 1gbit

---

### Post by bapoumba on 2014-07-14
Well, what you could do is open another terminal window and run **top**. May be you'll see other processes that are keeping the system busy and apt-get waiting.
Do you have internet access via a browser for ex during that waiting time ? Are you behind a proxy ?

---

### Post by ashley8 on 2014-07-14
The system is essentially idle.
If I go to install an app it says it takes 4-5 mins on that one host the rest connect instantly.
If I could figure out what sort of reset it went through daily I could recreate to diagnose easier.

---

### Post by bapoumba on 2014-07-14
Well, either apt hangs or its connection to the repos hangs. Could be uneasy to troubleshoot, as apt logs its actions in /var/log/apt/history.log and term.log and dpkg in var/log/dpkg.log, but they only keep their package maintenance actions.
You could have a look at /var/log/syslog and search for networkmanager, and see if there is anything strange around the timing of your update :
```
grep -i networkmanager /var/log/syslog
```

---

### Post by ashley8 on 2014-07-14
I have a 2nd system doing the same now....
I have an strace for this one though...

```
open("/usr/share/locale/en_GB/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_GB/LC_MESSAGES/apt.mo", O_RDONLY) = 7
fstat(7, {st_mode=S_IFREG|0644, st_size=9077, ...}) = 0
mmap(NULL, 9077, PROT_READ, MAP_PRIVATE, 7, 0) = 0x7fb5c95d1000
close(7)                                = 0
open("/usr/share/locale-langpack/en/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fb5c95d0000
0% [Working])        = 14]", 14
select(7, [5 6], [], NULL, {0, 500000}) = 1 (in [5], left {0, 499999})
read(5, "102 Status\nURI: http://security."..., 64000) = 126
select(7, [5 6], [], NULL, {0, 499999}) = 1 (in [6], left {0, 499685})
read(6, "102 Status\nURI: http://archive.u"..., 64000) = 115
select(7, [5 6], [], NULL, {0, 499685}) = 1 (in [6], left {0, 484451})
read(6, "102 Status\nURI: http://archive.u"..., 64000) = 140
select(7, [5 6], [], NULL, {0, 484451}) = 1 (in [5], left {0, 460311})
read(5, "102 Status\nURI: http://security."..., 64000) = 151
select(7, [5 6], [], NULL, {0, 460311}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)] [Connecting to s) = 93
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)] [Connecting to s) = 80
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)] [Connecting to s) = 80
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)] [Connecting to s) = 80
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)] [Connecting to s) = 80
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)] [Connecting to s) = 80
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)] [Connecting to s) = 80
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)] [Connecting to s) = 80
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0

```


it repeats those 4 lines every second...

The logs look clear

Perhaps the timeout is too low, they do flow pretty rapidly on screen

---

### Post by bapoumba on 2014-07-14
Not being much in networking stuff. Looks like an IPV6 address to me. Does that ring a bell ?
```
Connecting to archive.ubuntu.com (2001:67c:1360:8c01::18)
```
Will look around.

---

### Post by ashley8 on 2014-07-14
yes thats an ipv6 address, its like ipv4 but better :)

---

### Post by bapoumba on 2014-07-14
[http://ubuntuforums.org/showthread.php?t=2135862&page=3](http://ubuntuforums.org/showthread.php?t=2135862&page=3)
Post #28 :
> Applications that doesn't use an internal DNS cache are affected on every request (like apt and wget)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=611891](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=611891)
[https://lists.ubuntu.com/archives/ubuntu-users/2011-November/253677.html](https://lists.ubuntu.com/archives/ubuntu-users/2011-November/253677.html)

Will need some further looking around, this information may not be current..

---

### Post by ashley8 on 2014-07-14
Ohh....  Thanks bapoumba I think we're onto something.
I think the IPv6 repos are down....

```
ping6 google.com -n
PING google.com(2607:f8b0:4006:809::1000) 56 data bytes
64 bytes from 2607:f8b0:4006:809::1000: icmp_seq=1 ttl=57 time=1.61 ms
64 bytes from 2607:f8b0:4006:809::1000: icmp_seq=2 ttl=57 time=1.62 ms
64 bytes from 2607:f8b0:4006:809::1000: icmp_seq=3 ttl=57 time=1.65 ms


~$ ping6 archive.ubuntu.com -n
PING archive.ubuntu.com(2001:67c:1360:8c01::19) 56 data bytes
--- archive.ubuntu.com ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7054ms


~$ ping6 archive.ubuntu.com -n
PING archive.ubuntu.com(2001:67c:1360:8c01::18) 56 data bytes
--- archive.ubuntu.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms


telnet -6 www.google.com 80
Trying 2607:f8b0:4006:809::1013...
Connected to www.google.com.
Escape character is '^]'.


telnet -6 archive.ubuntu.com 80
Trying 2001:67c:1360:8c01::18...
(no connection after 2 mins)

```

---

### Post by ashley8 on 2014-07-14
Perhaps a coincidence but the IPv4 route goes to nlayer,  then to qwest then pnap to destination.
IPv6 stops at nlayer, though i know they dont have to go the same way.... perhaps its nothing.

```
tcptraceroute6 archive.ubuntu.com 80
traceroute to archive.ubuntu.com (2001:67c:1360:8c01::18) from <REMOVED>, port 80, from port 59021, 30 hops max, 60 bytes/packet
1  <REMOVED>  0.767 ms  0.667 ms  0.745 ms
 2  <REMOVED>  0.241 ms  0.266 ms  3.941 ms
 3  <REMOVED>  2.761 ms  5.009 ms  5.434 ms
 4  <REMOVED>  1.243 ms  1.196 ms  1.252 ms
 5  xe-2-0-0.cr2.iad1.us.nlayer.net (2001:590::4516:8e25)  7.490 ms  7.523 ms  28.375 ms
 6  xe-3-3-0.cr1.atl1.us.nlayer.net (2001:590::4516:8e69)  19.748 ms  23.804 ms  19.760 ms
 7  ae8-569.cr1.lax2.us.nlayer.net (2001:590::4516:8ede)  75.939 ms  72.919 ms  *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
^C43% completed...



traceroute6 archive.ubuntu.com
traceroute to archive.ubuntu.com (2001:67c:1360:8c01::18) from <REMOVED>, port 33434, from port 59018, 30 hops max, 60 bytes/packet
 1  <REMOVED>  0.734 ms  0.668 ms  0.633 ms
 2  <REMOVED>  21.597 ms  0.237 ms  5.121 ms
 3  <REMOVED>  2.589 ms  2.800 ms  2.192 ms
 4  <REMOVED>  35.159 ms  1.230 ms  1.235 ms
 5  xe-4-1-1.cr1.atl1.us.nlayer.net (2001:590::4516:8e8c)  46.435 ms  18.466 ms  19.990 ms
 6  xe-5-2-0.cr1.iah1.us.nlayer.net (2001:590::4516:8e75)  88.842 ms  32.604 ms  32.950 ms
 7  * * *
 8  * * *
 9  * * *
^C33% completed...


```

---

### Post by bapoumba on 2014-07-15
@ashley8 : would moving your thread to Networking suit you ? The issue is how apt connects to the repos using IPV6. May be some people there will know better that I do.
Have you had this problem before ? I mean, using IPV6 with apt or is this something recent ?

---

### Post by ashley8 on 2014-07-15
@bapoumba  yes I think thats a good idea, perhaps updating the thread topic too, any idea how I do this?

 they used to work fine, the boxes have been idle for a few months, now I want to update and use them I find they don't work

---

### Post by bapoumba on 2014-07-15
*Thread moved to **Networking & Wireless**.*
Thread title edited to include IPV6.

---

### Post by ashley8 on 2014-07-15
Ticket submitted to GTT (nlayer)

---

### Post by bapoumba on 2014-07-15
Would you mind giving a link ? (what do you call a ticket ? A bug report ?)

---

### Post by ashley8 on 2014-07-15
An incident ticket via email.
I outlined the connectivity issues.

They lost the first ticket... then they called me to say I need to submit a ticket with my direct peer and they will submit a ticket with GTT and then they will look at my ticket.

Seems odd to ignore a core routing issue because you haven't got a ticket from a specific person.

---

### Post by ashley8 on 2014-07-16
So an update,
A ticket has to be raised;
1) by me to my hosting company
2) by my hosting company to the datacentre
3) by the datacentre to the carrier
4) by the carrier to upstream carrier (GTT)

all so that the upstream carrier can look at what looks to be a huge routing.
Talk about red tape getting in the way of providing service...

Sigh

---

### Post by bapoumba on 2014-07-16
Wow, my best brainwaves over to you :)

---

### Post by ashley8 on 2014-07-17
So Ive now opened a ticket with everyone.
My provider (who will remain nameless for now) has denied that the ubuntu servers work with IPv6. 
Quote "The IPv6 on the Ubuntu mirrors has never worked in the past."

 So I would appreciate some traceroutes, pings an telnet/curls of the IPv6 archive.ubuntu.com site (2001:67c:1360:8c01::18  or 2001:67c:1360:8c01::19) from any of you that have working or broken IPv6 connections to the ubuntu servers, if broken please provide a working trace to google or something. 
I have provided them with 3rd party ipv6 testing tools, but some independent traceroutes from you guys may help a lot.

Thanks!!

---

### Post by bapoumba on 2014-07-18
From what I can see and test, my ISP (and the router they ship) do not provide IPV6 support.

---

### Post by ashley8 on 2014-07-22
[SOLVED]
ISP eventually accepted there was an issue and rerouted traffic. 
 Perfect connectivity since. 
Good News The IPv6 repos work once again!!

---

### Post by bapoumba on 2014-07-22
Woohoo !
Please mark your thread as solved (under Thread Tools), thanks :)

---

