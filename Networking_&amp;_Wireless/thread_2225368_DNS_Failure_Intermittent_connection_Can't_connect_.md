---
title: "DNS Failure? Intermittent connection? Can't connect to multiple DNS servers."
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2014-05-21
[FONT=arial][COLOR=#000000]Basic problem -- I can't connect to websites consistently. And Chrome tells me it is a DNS lookup failure.
[/COLOR]
[COLOR=#000000]My setup -- Linux, kubuntu 12.04. Asus P8Z68-V/Gen3 Motherboard, which has Intel82579 LAN.[/COLOR]
[COLOR=#000000]
Detailed Problem -- I'm on a university internet connection at work. I frequently can not connect to any website. When I let it time out on Chrome, it tells me there is a DNS error.[/COLOR]
[COLOR=#000000]LOTS of time, like 70% of the time, I can't connect to any of the google services. But I can still use other websites. For example, I can't search on google, but I can search on duckduckgo.[/COLOR]
[COLOR=#000000]But sometimes I still can't even reach ANY website. 

However, this is not an 'all the time' problem. I will have spotty connection for maybe 3 hours one morning, then no problems all afternoon and even the next day. But then the 3rd day I'll have issues for 4 hours in the afternoon. Then the next day for 2 hours around lunch. etc, etc. Its not consistent in the timing or duration at any point in time.[/COLOR]
[COLOR=#000000]
During the 2,3,4 hours it is spotty, its not gone the entire time. I'll have 30 seconds where I can not connect, then it will come back for a few minutes. Then I'll have a couple minutes of poor connection (i.e. not connecting to google chat in pidgin, or not being able to search google, or sometimes its not connecting to anything even non-google sites) and then it will work again normally.[/COLOR]
[COLOR=#000000]
I've tried chaning my DNS servers from my school's, to google's DNS to OpenDNS. I have the same issues on all of them.[/COLOR]
[COLOR=#000000]
I've had school tech support look at it, and they tell me nothing is wrong on their end. No one else in my lab has similar issues on their computers.[/COLOR]
[COLOR=#000000]
I just re-installed kubuntu 12.04 last week fresh from a CD. Still same issues. I run kubuntu 12.04 at home on 3 computers with zero issues.[/COLOR]
[COLOR=#000000]
I don't even know how to troubleshoot this crazy issue. I've tried ping and tracerout. They either come back looking normal, or they time out and give me no results.[/COLOR]
[/FONT][COLOR=#000000][FONT=Segoe UI][FONT=arial]Other times I get errors. For example. I can load a BBC News page, and it immediately loads. Then do a traceroute on [www.google.com]("http://www.google.com/"), and I get errors.  Here is an example of doing a traceroute on bing, then google with it failing.  Then just a couple seconds later I immediately do it again on google, and it works.  

These three commands were run immediately after each other, no waiting time more than a couple seconds.[/FONT]

[/FONT][/COLOR]```

[COLOR=#000000][FONT=Courier New]me@myhost:~$ traceroute www.bing.com
traceroute to www.bing.com (204.79.197.200), 30 hops max, 60 byte packets
1  kc6-vl579.net.ohio-state.edu (128.146.132.1)  0.810 ms  0.780 ms  0.769 ms
2  kc1-teng8-1.net.ohio-state.edu (164.107.2.18)  0.736 ms  0.703 ms  0.717 ms
3  kc3-teng1-1.net.ohio-state.edu (164.107.2.193)  0.724 ms  0.718 ms  0.695 ms
4  clmbk-r9-xe-1-0-1s330.core.oar.net (199.18.169.1)  1.006 ms  1.222 ms  1.224 ms
5  clmbn-r0-xe-1-2-0s100.core.oar.net (199.218.38.25)  0.942 ms  0.945 ms  0.937 ms
6  clmbn-r5-xe-4-2-0s100.core.oar.net (199.218.38.13)  1.178 ms clmbn-r5-xe-4-3-0s100.core.oar.net (199.218.38.17)  1.09
3 ms clmbn-r5-xe-4-2-0s100.core.oar.net (199.218.38.13)  1.050 ms
7  toldb-r5-et-1-0-0s100.core.oar.net (199.218.39.250)  4.104 ms  4.097 ms  4.063 ms
8  chi-8075.msn.NET (206.223.119.27)  20.862 ms  20.875 ms  20.857 ms
9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
me@myhost:~$ traceroute www.google.comwww.google.com: Name or service not known
Cannot handle "host" cmdline arg `www.google.com' on position 1 (argc 1)
me@myhost:~$ traceroute www.google.com
traceroute to www.google.com (74.125.225.113), 30 hops max, 60 byte packets
1  kc6-vl579.net.ohio-state.edu (128.146.132.1)  0.723 ms  1.032 ms  1.037 ms
2  kc1-teng8-1.net.ohio-state.edu (164.107.2.18)  0.691 ms  0.671 ms  0.991 ms
3  kc3-teng1-1.net.ohio-state.edu (164.107.2.193)  1.353 ms  1.346 ms  1.336 ms
4  clmbk-r9-xe-1-0-1s330.core.oar.net (199.18.169.1)  1.298 ms  1.295 ms  1.285 ms
5  clmbn-r0-xe-1-2-0s100.core.oar.net (199.218.38.25)  1.288 ms  1.280 ms  1.271 ms
6  clmbn-r5-xe-4-2-0s100.core.oar.net (199.218.38.13)  1.262 ms clmbn-r5-xe-4-3-0s100.core.oar.net (199.218.38.17)  1.041 ms 0.999 ms
7  toldb-r5-et-1-0-0s100.core.oar.net (199.218.39.250)  4.085 ms  4.120 ms  4.105 ms
8  192.35.170.50 (192.35.170.50)  13.817 ms  13.811 ms  13.771 ms
9  209.85.254.120 (209.85.254.120)  13.813 ms  13.796 ms  13.777 ms
10  209.85.240.150 (209.85.240.150)  14.402 ms  14.400 ms  14.675 ms
11  ord08s08-in-f17.1e100.net (74.125.225.113)  13.717 ms  13.712 ms  13.904 ms
me@myhost:~$[/FONT][/COLOR]
```[COLOR=#000000][FONT=Segoe UI]

[FONT=arial]I've also done a nslookup on google when I can't connect, and it says ""connection timed out; no servers could be reached".

No one else in my office has this problem, I can't for the life of me figure out where to go next or what to do?[/FONT][/FONT][/COLOR]

---

### Post by dannyboy79 on 2014-05-21
do you use network-manager? if so, disable dnsmasq within the NetworkManager.conf file by putting a # symbol in front of that line. This solved all my issues with weird or slow browsing

---

### Post by NertSkull on 2014-05-24
I don't use network manager.

I have everything set up in /etc/network/interfaces

---

### Post by NertSkull on 2014-07-24
My problem has finally been solved.  Turns out it was not me/linux/my computer's fault.  It was my work.

We used to all have static IPs here at work.  And recently they switched us all to DHCP.  I was left on a static IP so I could connect to my computer from home through SSH.  Turns out they forgot to switch one of the other computers to DHCP, and the static they assigned me happened to be the static that other computer already had.

So they just switched my static IP to a new number, and all is well.

---

