---
title: "Can’t ssh to my server"
date: 2021-08-23
forum: Networking &amp; Wireless
---

### Post by doeffgek on 2021-08-23
Hello everyone. 

I’m having a problem with the network connection of my server. I already have a Debian server running on a thin client that works great, but a lack of disk space and a secondary use for the server made me redo the whole thing. 

I installed a new server on a old pc, but now when it boots it asks for ip 255.255.255.255. Since I don’t know first thing about subnetting it leaves me stuck. Yesterday I could ssh into it using a normal 192168.2.x ip, but today for maintenance the power was cut for a while, and now I can’t get into it anymore from a remote client. 

when I type ‘ip a’ in both servers te results are basically the same except the 192.168 ip has a different 4th quarter. 
min my router the old server is listed as 192.168.2.x with dhcp, and the new one as 255.255.255.255 with static ip. Both machines are set up as dhcp with a /24 subnet. 

can anyone explain to me what went wrong with the settings? And even more important how to fix this….

many thanks in advance.

---

### Post by T.J. on 2021-08-25
It is quite likely that your system is not configured properly. I am afraid that your explanations are lacking needed details, though no fault of your own.  You can't possibly know everything getting started.

What I need from you to get started is an copy of the IP address details that DHCP (presumably your router) assigned. You probably do not need to worry about security, unless you are bridging. As a LAN address: 192.168.x; it means that your LAN is likely inaccessible from the outside; and you are in no danger to post the address details.

---

### Post by not-published on 2021-08-25
tdlp.org  the linux documentation project.org

NAG

network administration guide - you want the previous version explaining IPV4.  the older versions are extremely easy to read and effective and still work.  newer versions got cancel culture-sh and went off on tangents and ipv6 - avoid any version that isn't simple as pie.

rule #1 in NAG is you need to use ifconfig (check that your cards UP and have an IP), your routes (try routed(1) because it's easier), and put your IP in /etc/hosts.equiv.  doing that will NOT be secure but will ping and telnet.  The rest I will leave to NAG.  Modernly, Apple would use "bridging", IPV6, yp, and other things and have tools that do that stuff automatic and tools for sharing - which aren't going to fit on your older PC i'm assuming.

of course, you'd be better to switch to IPV6 and use more modern tools.  but i totally understand without asking why one would be avoiding doing so

In my view, IPV4 should have been made ANY-BIT (not 64 - huge mistake and will need to be 128 soon - and people said that), and the new "software" embedded in IPV6 is malware and they never DO publish what cloud server does what with IPV6, hack my delivery layer thanks.  However - I'm obviously out-voted !  So IPV6 is what you want believe me!

---

### Post by doeffgek on 2021-08-26
I got it working by simply setting static ip. Now everything&#8217;s working accept for one thing&#8230;
when booted ip after a power cut the ip is first set in 193.x.x.x range. You know the range that is set when the correct ip won&#8217;t set. But when I reboot again there&#8217;s no problem at all. Op is set to static on both server and router. 

anyone any guess how to solve?

---

