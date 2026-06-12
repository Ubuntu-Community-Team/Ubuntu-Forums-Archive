---
title: "Only &quot;Some&quot; Web Sites Load"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by sfhc on 2006-09-26
Hello,

I recently installed Ubuntu 6.06.

I am facing an unusual problem.  Only some Web Sites load.  For example (in both Firefox and Opera) if I type in [www.google.com](www.google.com), I get an error.  The error is can't find/connect to server.  If I type in Google's IP address I get a response, and the Web Site loads.

I think oh yeah, sounds like a DNS issue, as in Ubuntu does not have the correct (or any) DNS servers for my ISP.  I thought that because in past experiences only being able to view Web Sites by IP is usually solved by setting the DNS servers.

However, there is a twist. Some sites, such as amazon.com, any Ubuntu site, and a few random others, would load by their domain name just fine.

I check the DNS servers listed in Ubuntu, and they are fine.  Ubuntu correctly set the DNS servers.

This is a wierd twist, that some sites load, and others don't.  

Here is another twist, when I use ping, tracert, whois, etc... They work just fine, even on google.com, and other sites that don't load in the browser.

I tried wget, and got some strange results.  If I wget a site that will load by domain name in the browser, it works fine.  If I wget a site that does not load in the browser, this is what wget outputs:

```
wget www.google.com
resolve www.google.com 64.233.187.99

302 found index.html

resolve www.google.com 1.0.0.0
sending request index.html
connecting...
```

I don't know why the IP changes. Wget resolves the IP correctly to verify the presence of the file, but when it requests the file for download, the IP is wrong.  This seems like a hint as to what may be going wrong with the browsers also.

Since ping, tracert, etc... works on all domains, but for http requests only some sites work, I am totally stumped.

Also, updates work, apt-get works, and syncing to the time server works.

Anyone have any ideas?

Thanks!
-Jose

---

### Post by handy on 2006-09-26
You could try turning off **ipv6**?

In firefox do the following:

type **about:config** in the address field

then type **ipv6** in the new **filter:** field

then double click on the one & only line that is left in the ff viewing window, to change it's boolean value to **true**

Close firefox & restart it & see how you go?

Many of us though we have internet conection, can not browse the web without doing the above.

I hope that solves it for you...

---

### Post by sfhc on 2006-09-27
Hello Handy,

Thanks for the reply.  That was the correct solution.  Firefox can now load all Web Sites.

I imagine I need to make a similiar change in opera's settings to get it to be fully functional.

When I execute ifconfig, I get IPv6 information.  Do I need to disable IPv6 at the system level also?

Thanks again,
Jose

---

### Post by handy on 2006-09-27
I'm so glad you can browse now!

I only use firefox, but I believe that opera is based on the same code so try your luck with the **about:config** routine.

I don't have to dissable ipv6 system wide, since the Dapper release.

So if you can't get opera working any other way you may have to dissable it system wide.  If so search the forum, there are more than one way to do everything & some are more correct & sometime those ones are easier to do to...

[B]*[Edit:]*  By the way could you, or anyone else for that matter let us know here what you have to do to get Opera past the ipv6 problem?  It may help many others in the future... 

Thanks.[/B] 8)

---

### Post by sfhc on 2006-09-28
Hey,

Thanks it is great to have Firefox working!

I tried about:config in Opera, and got the config options, however, there is not an option for disabling ipv6 similiar to Firefox's.  I will keep looking.

As far as a system wide disabling, I think I am going to try it. I am also running Dapper.

Here is what I have done so far:
1. Edit hosts - comment out ipv6 lines
2. Modify etc/modprobe.d/alias 
   alias net-pf-10 ipv6 off
   alias ipv6 off
3. Modify etc/modprobe.d/blacklist
   blacklist ipv6
3-alternlate. Some say you can also create a file in modprobe.d named blacklist-ipv6 and put the blacklist ipv6 line in the file for the same effect.

Will post more if I find a ipv6 solution specific to Opera.

-Jose

---

### Post by sfhc on 2006-09-28
The system wide disabling of ipv6 solved the problem with opera, indirectly. 

I went through the opera about:config and the actual .ini files, it appears that there may not actually be a method of disabling ipv6 as you can in Firefox.

Anyway, I am happy to have all the browsers working now.

---

### Post by handy on 2006-09-28
Thanks for your valuable feedback sfhc! :)

---

### Post by racmar on 2007-03-20
Thank you soooo much.  I've been having problems /w [www.etrade.com](www.etrade.com) since I've upgraded to edgy.  Now, it just dawned on my why, and I found your post.  Anyway, I am one happy camper again.

---

### Post by pravin on 2007-04-17
I have a similar problem. After turning off ipv6 in firefox, all web sites work.

However, other internet applications like gaim keep timing out :(

---

### Post by aztektum on 2007-04-20
I'm having this problem on a fresh Feisty install I did at work. I disabled all the ipv6 but still having issues loading "some" web pages.

---

### Post by oedenfield on 2007-04-23
I just installed Feisty and have the same issue.  I had it with a previous install of Edgy.  Tried the mentioned Firefox ipv6 changes.  I also looked into the MTU and the MTU of my router and my Feisty install are both 1500.

---

### Post by oedenfield on 2007-04-25
I have tried a number of things including:

Turn off IPV6 in Firefox and system-wide
Changes to /etc/sysctl.conf

TCP WMEM, TCP RMEM:
net.ipv4.tcp_wmem = 4069 16384 131072
net.ipv4.tcp_rmem = 4069 87380 174760

TCP Window Scale:
net.ipv4.tcp_default_win_scale = 0

My ifconfig is:
```
eth0      Link encap:Ethernet  HWaddr 00:13:D4:3B:9F:BE  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe3b:9fbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:42 dropped:0 overruns:0 frame:42
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10008 (9.7 KiB)  TX bytes:26570 (25.9 KiB)
          Interrupt:21 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```


My traceroute to [www.google.com](www.google.com) is:
```
Hop	Hostname					IP			Time1
1	desktop1202.local				192.168.0.100		0.142ms
1	192.168.0.1					192.168.0.1		asymm
2	user-69-73-66-129.knology.net		69.73.66.129		12.524ms
3	24.214.0.174					24.214.0.174		15.144ms
4	user-24.96.198.49.knology.net			24.96.198.49		13.611ms
5	user-24.96.198.41.knology.net			24.96.198.41		asymm
6	user-24.96.68.125.knology.net			24.96.68.125		asymm
7	atl.a00.ge-4-0.33.knology.wvfiber.net		63.223.8.133		asymm
8	no						reply			*
9	no						reply			*
10	no						reply			*
11	no						reply			*
12	no						reply			*
13	no						reply			*
14	no						reply			*
15	no						reply			*
16	no						reply			*
17	no						reply			*
18	no						reply			*
19	no						reply			*
20	no						reply			*
21	no						reply			*
22	no						reply			*
23	no						reply			*
24	no						reply			*
25	no						reply			*
26	no						reply			*
27	no						reply			*
28	no						reply			*
29	no						reply			*
30	no						reply			*
31	no						reply			*
```


Pinging my router:
```
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=0.447 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=0.466 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=0.456 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=0.471 ms
^[64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=0.461 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=127 time=0.471 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=127 time=0.447 ms

--- 192.168.0.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6002ms
rtt min/avg/max/mdev = 0.447/0.459/0.471/0.029 ms
```

Pinging [www.google.com:](www.google.com:)
```
PING www.l.google.com (64.233.161.147) 56(84) bytes of data.
64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=1 ttl=244 time=43.4 ms
64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=2 ttl=244 time=45.3 ms
64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=3 ttl=244 time=44.6 ms
64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=4 ttl=244 time=52.3 ms
^[64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=5 ttl=244 time=41.4 ms
64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=6 ttl=244 time=42.2 ms
64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=7 ttl=244 time=44.6 ms
64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=8 ttl=244 time=38.5 ms
64 bytes from od-in-f147.google.com (64.233.161.147): icmp_seq=9 ttl=244 time=39.2 ms

--- www.l.google.com ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8003ms
rtt min/avg/max/mdev = 38.563/43.563/52.394/3.849 ms
```


Netstat, Routing Table:
```
Destination			Gateway		Netmask		Interface
192.168.0.0			0.0.0.0			255.255.255.0		eth0
169.254.0.0			0.0.0.0			255.255.0.0		eth0
0.0.0.0				192.168.0.1		0.0.0.0			eth0
::1				::			128			lo
fe80::213:d4ff:fe3b:9fbe	::			128			lo
fe80::				::			64			eth0
ff00::				::			8			eth0
```


MTU in Ubuntu is 1500 and MTU on router is 1500.  When using DHCP I can get to the Google sites (see below) but when static (as the same IP that DHCP gives me) I can't access any sites.

In Firefox, I can always get to Google and Google-run sites (Image search, Blogger, Gmail, Google Groups).  All other sites I've tried (CNN.com, digg.com, wikipedia.org) all fail to load (status bar does say that sit has been communicated with but it never moves from there)

I use OpenDNS as the DNS on my D-Link DI-614+ router, OpenDNS is as follows:
	208.67.222.222
	208.67.220.220

I currently dual-boot between Windows XP and now Feisty Fawn and I'd love to leave Windows and use Ubuntu more, but this needs to be fixed before I can do so.  I have tried to search and find everything I could before making this post.  Sorry if it is a little long.

Thank you for all of your help.  Being new to Ubuntu, it makes me feel good when I see a forums as active as this site is, active with people helping each other.

Thank you again.

---

### Post by oedenfield on 2007-04-27
I booted into Ubuntu yesterday evening and what do you know, the internet is working.  Others have reported this, I just makes me wonder what was actually going on.  I did nothing different yesterday then I did a few days ago after first installing.  At any rate it is working now, but hopefully I won't be broke again after a restart (which may happen today because of weather).

Thank you.

---

### Post by Ubuntu Warrior on 2007-07-22
Seems I have the very same problem on Feisty i.e. some sites I can get to no problem others not, but the sites I cannot get to seem to be fine at some later stage - weird!

I have tried turning off ipv6 at system level and turning it off at FF level but still no joy. Could this be some sort of virus? Rouge Java code?

---

### Post by oedenfield on 2007-07-22
I continue to have the problem and have only found one way around it with my setup.  

For some reason if I disconnect power from my computer, router and cable modem and let them sit for about 20 minutes and then turn them all on and let Feisty load..   everything will work perfectly.  If I boot into Feisty right after Windows I experience the problem.

That is the only work around I've found for my setup.  I'm looking forward to Gutsy for that reason and for more video support for my Radeon 9250.

---

