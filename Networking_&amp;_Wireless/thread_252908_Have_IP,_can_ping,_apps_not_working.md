---
title: "Have IP, can ping, apps not working"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by pahool on 2006-09-07
I have just installed Ubuntu 6.06 on a Dell 700m laptop. I am successfully getting an IP address through a wired connection. I am connecting to my DNS server ok (nslookup works.) Ping works fine for both LAN addresses and Internet addresses (I can ping google, yahoo successfully)

However I can not use applications such as firefox or ssh successfully. All attempts just hang.

I have already edited the ipv6 line in /etc/modprobe.d/aliases

to: 

alias net-pf-10 off #ipv6

and rebooted. That has not helped.

I have the machine set up as a dual-boot machine with Windows XP and when I boot into Windows I get the same IP address from our university dhcp server, but everything works fine. The Broadcast and subnet mask settings are correct in ubuntu as well.

Anyone have any ideas on what might be wrong here?

---

### Post by kostkon on 2006-09-07
What about a proxy server? Maybe is a proxy problem as you refered to Firefox not connecting. What do you think?

---

### Post by pahool on 2006-09-07
Not a proxy problem. We don't use a proxy server here and firefox is configured for a direct connection.

It's not just firefox, it's pretty much all network applications that aren't working (ftp, sftp, ssh, telnet) The only things that are working are ping and nslookup.

---

### Post by tbonius on 2006-09-07
And you can ping outside of your internal network?  This doesnt make any sense.  When you use nslookup/dig.. are you looking up external domain name spaces (yahoo.com.. etc..)?  Are you pinging external name spaces such as yahoo.com?

Try running a tcpdump (or ethereal) on that interface while trying to open and run Firefox.. then post the filtered results for your application.

T

---

### Post by pahool on 2006-09-07
The following are the results of an ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:AF:70:FA
          inet addr:128.125.236.68  Bcast:128.125.236.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5988623 (5.7 MiB)  TX bytes:883247 (862.5 KiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

Here's the results of tcpdump when I filter for the host "www.stomatopod.com" and then try to open that host in firefox:

pahool@pahool-laptop:~$ sudo tcpdump host [www.stomatopod.com](www.stomatopod.com)
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
15:49:08.623773 IP dynamic-236-068.usc.edu.38051 > apache2-jolly.nilla.dreamhost.com.www: S 4180793017:4180793017(0) win 5840 <mss 1460,sackOK,timestamp 1340627 0,nop,wscale 2>
15:49:11.612340 IP dynamic-236-068.usc.edu.38051 > apache2-jolly.nilla.dreamhost.com.www: S 4180793017:4180793017(0) win 5840 <mss 1460,sackOK,timestamp 1341377 0,nop,wscale 2>
15:49:17.612867 IP dynamic-236-068.usc.edu.38051 > apache2-jolly.nilla.dreamhost.com.www: S 4180793017:4180793017(0) win 5840 <mss 1460,sackOK,timestamp 1342877 0,nop,wscale 2>
15:49:29.613659 IP dynamic-236-068.usc.edu.38051 > apache2-jolly.nilla.dreamhost.com.www: S 4180793017:4180793017(0) win 5840 <mss 1460,sackOK,timestamp 1345877 0,nop,wscale 2>


tcpdump output for an ssh attempt:

pahool@pahool-laptop:~$ sudo tcpdump host cassandra.usc.edu
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
15:51:36.762249 IP dynamic-236-068.usc.edu.53677 > cassandra.usc.edu.ssh: S 44702723:44702723(0) win 5840 <mss 1460,sackOK,timestamp 1377662 0,nop,wscale 2>
15:51:39.761787 IP dynamic-236-068.usc.edu.53677 > cassandra.usc.edu.ssh: S 44702723:44702723(0) win 5840 <mss 1460,sackOK,timestamp 1378412 0,nop,wscale 2>
15:51:45.762130 IP dynamic-236-068.usc.edu.53677 > cassandra.usc.edu.ssh: S 44702723:44702723(0) win 5840 <mss 1460,sackOK,timestamp 1379912 0,nop,wscale 2>
15:51:57.762724 IP dynamic-236-068.usc.edu.53677 > cassandra.usc.edu.ssh: S 44702723:44702723(0) win 5840 <mss 1460,sackOK,timestamp 1382912 0,nop,wscale 2>

---

### Post by pahool on 2006-09-07
I should add that for both of the above examples, the messages are being spit out of tcpdump every five seconds or so, and the applications are just timing out eventually. Firefox is giving "The connection has timed out" error, rather than a "Server not found" error.

---

### Post by pahool on 2006-09-07
Here are the verbose results of attempting an ssh session:

pahool@pahool-laptop:~$ sudo tcpdump -v host cassandra.usc.edu
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
15:54:51.169275 IP (tos 0x0, ttl  64, id 30497, offset 0, flags [DF], proto: TCP (6), length: 60) dynamic-236-068.usc.edu.49842 > cassandra.usc.edu.ssh: S, cksum 0xe6dc (correct), 252753013:252753013(0) win 5840 <mss 1460,sackOK,timestamp 1426260 0,nop,wscale 2>
15:54:54.165834 IP (tos 0x0, ttl  64, id 30498, offset 0, flags [DF], proto: TCP (6), length: 60) dynamic-236-068.usc.edu.49842 > cassandra.usc.edu.ssh: S, cksum 0xe3ee (correct), 252753013:252753013(0) win 5840 <mss 1460,sackOK,timestamp 1427010 0,nop,wscale 2>
15:55:00.166117 IP (tos 0x0, ttl  64, id 30499, offset 0, flags [DF], proto: TCP (6), length: 60) dynamic-236-068.usc.edu.49842 > cassandra.usc.edu.ssh: S, cksum 0xde12 (correct), 252753013:252753013(0) win 5840 <mss 1460,sackOK,timestamp 1428510 0,nop,wscale 2>
15:55:12.166869 IP (tos 0x0, ttl  64, id 30500, offset 0, flags [DF], proto: TCP (6), length: 60) dynamic-236-068.usc.edu.49842 > cassandra.usc.edu.ssh: S, cksum 0xd25a (correct), 252753013:252753013(0) win 5840 <mss 1460,sackOK,timestamp 1431510 0,nop,wscale 2>
15:55:36.168553 IP (tos 0x0, ttl  64, id 30501, offset 0, flags [DF], proto: TCP (6), length: 60) dynamic-236-068.usc.edu.49842 > cassandra.usc.edu.ssh: S, cksum 0xbaea (correct), 252753013:252753013(0) win 5840 <mss 1460,sackOK,timestamp 1437510 0,nop,wscale 2>

---

### Post by tbonius on 2006-09-07
But yet you can ping these hosts?

---

### Post by pahool on 2006-09-08
Well, I'm at home now (I was at work previously) and everything's working fine. I can't figure out what's wrong with the connection at work. The jack is active and works fine when I boot into Windows XP. But nothing works on Linux. I'll have to keep trying...

---

