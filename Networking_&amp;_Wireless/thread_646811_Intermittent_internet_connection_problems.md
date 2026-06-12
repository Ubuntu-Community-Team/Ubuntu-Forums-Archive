---
title: "Intermittent internet connection problems"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by cadlewv on 2007-12-21
I have a Westell router/modem from Verizon.  I use a WG111v2 USB wireless adapter from Netgear (works out of the box).  

When I start up Ubuntu and Firefox, I get a connection.  But sooner rather than later, it drops.  I can reconnect sometimes, but it will dop the connection again.

Works fine in XP, so I'm assuming there's a problem with a setting or two in Ubuntu.  I have changed no network settings since installation.  Everything is on default.  

I do have to key in my WEP password each time I log on though.  Not sure if that has anything to do with it.

Any suggestions or advice would be appreciated.

And, I must say, I have flirted with different distros of linux here and there, and am very happy with this one.  I do believe that this one will enable me to migrate everything over the next several months so that I can use Linux exclusively.

Thanks.

---

### Post by cadlewv on 2007-12-22
Anyone?

---

### Post by monkeyking on 2007-12-22
try, disabling security to see if that is the error,
if that doesn't work, go for ndiswrapper

---

### Post by cadlewv on 2007-12-24
I don't think I have anything additional for security.  No AV or FW installed.

What will NDISWrapper do?

---

### Post by monkeyking on 2007-12-24
ndiswrapper let's you use windows xp drivers.
search for ndiswrapper on the forum.

---

### Post by cadlewv on 2007-12-24
I actually already have it downloaded.  Is there anything in particular I need to do when installed?

Does this sound like what the problem could be?  I mean, it connects just fine.  But within minutes, sometimes seconds, the connection is gone.

---

### Post by cadlewv on 2007-12-24
Ok, I've searched and found a thread about installing ndiswrapper.  Of course, it seems that nothing ever works as it's supposed to.  After (supposedly) installing it, I checked to make sure it was installed 'ndiswrapper -v' and it wasn't.  I reapeated the steps a few times with the same result.

I'm a very patient person that's getting very frustrated now.  I've tried different distros here and there over the years.  I was very hopeful that someone had finally come out with a distro that just 'worked' (or at least 'almost worked').  I am about at the point of giving up for another year or so.

If nothing else, even a linux distro should, at very basic, not make it near impossible to connect to the internet.

Any instructions anyone has really need to be in the format of 'put your left foot in front of your right one, then your right in front of your left', etc.  Very basic, easy to understand, step-by-step instructions, please.

Thanks for the help so far.

---

### Post by mellowd on 2007-12-24
Open up a terminal and type this:

```
ifconfig
```

then in the same terminal type this:

```
sudo aptitude install traceroute
traceroute www.google.com
```

paste the results of ifconfig and traceroute here so we can have a look

---

### Post by cadlewv on 2007-12-24
This is what it gives me while the internet connection is up:

traceroute to [www.google.com](www.google.com) (64.233.169.104), 30 hops max, 40 byte packets
 1  dslrouter (192.168.1.1)  4.774 ms  9.060 ms  13.672 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  yo-in-f104.google.com (64.233.169.104)  36.356 ms  38.669 ms *

---

### Post by mellowd on 2007-12-24
Hmm, I've noticed a lot of people are having problems with the wireless seeming to disconnect all the time. Unfortunately off the top of my head I don't have a solution but there are tons of threads in the wireless section with this exact same problem, you could take a look there.

In the meantime, you could also check the log on your wireless router if possible, see if there is anything there which could explain why it's dropping you.

---

### Post by cadlewv on 2007-12-24
I -am- already in the wireless section.  My router doesn't drop me while I am in XP, only in Gutsy.  This is an Ubuntu specific problem.

---

### Post by mellowd on 2007-12-24
> **cadlewv said:**
> I -am- already in the wireless section.  My router doesn't drop me while I am in XP, only in Gutsy.  This is an Ubuntu specific problem.

well then have you --checked-- any other thread where this is a similar problem? Have you even bothered to check the router or just assumed?

---

### Post by cadlewv on 2007-12-24
I have been checking this non-stop since I posted the thread initially.  And, yes, I have assumed that my router is fine, since I"m using it right now.  Some things can be ruled out by consistency (i.e. always works with XP, never works (after 1st minute) with Gutsy).

---

### Post by mellowd on 2007-12-24
> **cadlewv said:**
> I have been checking this non-stop since I posted the thread initially.  And, yes, I have assumed that my router is fine, since I"m using it right now.  Some things can be ruled out by consistency (i.e. always works with XP, never works (after 1st minute) with Gutsy).

Though the router could be receiving a packet it doesnt like and dropping the connection, you never know. Always check everything

---

### Post by cadlewv on 2007-12-24
But since you asked, here are the results from the ifconfig and traceroute commands.

ifconfig results when down:

mark@mark-ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:50:8D:85:52:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:89 (89.0 b)  TX bytes:89 (89.0 b) 

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:B3:0E:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:1663 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2660 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:702049 (685.5 KB)  TX bytes:329809 (322.0 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-14-6C-B3-0E-BB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

traceroute results when down:

mark@mark-ubuntu:~$ traceroute [www.google.com](www.google.com) 
[www.google.com:](www.google.com:) Name or service not known 
Cannot handle "host" cmdline arg `[www.google.com](www.google.com)' on position 1 (argc 1)

---

