---
title: "VERY slow Internet - Internet was speedy for months till last week"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by memories on 2008-06-23
During the past few days, almost suddenly, my Internet came very slow. As far as I can tell, it's not a problem with my settings or machine. 

I have wireless, and both wifi and wired connections are slow. Nobody on the network is downloading anything, Bittorrent isn't on, etc. 

It feels like dial up, and the problem looks like it might be affecting my upload more than my download. Downloading files is around 50-80KB/sec (normally a few hundred), but sites take awfully long to load. It's not a DNS problem because IP addresses accessed directly aren't any faster. 

Everything is effected. Browsing, IRC/chat, SSH, etc. 

When I SSH into my remote machines, I literally have a delay between each letter I type. 


My ISP says everything is fine on their end. I have not shut down my compture to rule out the possiblity that the problem is fro my machine. I also have no restarted the router/modem. 

I cannot because this is a work machine and it is hosting some services. I *did* shut down each service one by one and found that none of them are causing the problem. 

Here's my question: How can I find out what network processes are using the most bandwidth and how many connections are open? Besides netstat, what can I do to diagnose this and make sure it's not resulting from my machine only (which i highly doubt, Verizon DSL probably _does_ suck this bad).

---

### Post by beckols on 2008-06-23
A good program for instant network analysis is iftop, it is also very lightweight and has ASCII bars showing how much bandwidth each connection is using.  To discover trends, and for more readable output (but not so much instantaneous info) ntop is awesome.  It has a web interface with graphs and many different options to view network traffic. I would try iftop first to see if you can discern the source of the heavy usage, but if it doesn't clarify things, I would definitely recommend ntop.

---

### Post by str8line on 2008-08-11
With DSL if your connection is running slow, look to the physical setup.  

How long is the DSL phone cable (must be less than 14ft), are all phones, fax machines, satellite dishes filtered.  

Check for your time zone in both the pc and the modem/router and ensure set to the correct time zone for your location.

Hope this helps.

Chris Powell
Lemming CIR
London, ON

---

