---
title: "[SOLVED] Machine on wired network won't reach Internet in a useful way"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by deelux523 on 2007-12-12
My Gutsy desktop won't reach the internet in a useful way via its wired connection.

_HERE'S THE BAD NEWS_
With the desktop network configuration set to **Roaming Mode** OR to **DHCP**
Firefox keeps telling me that it is...
"Unable to connect: Firefox cannot establish a connection to the server at [Website]."
Other internet dependent apps are equally useless, i.e. Update Manager, the weather widget, etc.

_HERE'S THE GOOD NEWS_
I can successfully ping my **wireless router/hub**
I can successfully ping my **dsl modem**
I can successfully ping **[www.google.com](www.google.com)**
I can successfully use** SAMBA to look into the desktop** machine's shares from the other machine (laptop) on the network
I can successfully ping** the other machine** (laptop) on my network
I can successfully ping my **desktop machine from the other machine** (laptop) on my network

_MORE GOOD NEWS_
My laptop (dual boot Gutsy & XP) can reach the internet from either OS. Otherwise I wouldn't be posting this.

Based on my reading some other posts, here is the output from **ifconfig**:
> eth0      Link encap:Ethernet  HWaddr 00:50:DA:21:40:FF  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:1 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29988 (29.2 KB)  TX bytes:8330 (8.1 KB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

          RX bytes:56144 (54.8 KB)  TX bytes:56144 (54.8 KB)

Here is the output from **dhclient**:
> user_xyz@machine_abc:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:da:21:40:ff
Sending on   LPF/eth0/00:50:da:21:40:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 36584 seconds.

Please let me know if there are any other diagnostics I can run to provide more info.
Thanks in advance for any insights!
DL

---

### Post by manthony121 on 2007-12-12
It is odd that you can 'ping' an external host, such as "www.google.com", but Firefox can't connect to it.  Can you ping other common sites ([www.ubuntu.com](www.ubuntu.com), etc)?  Does FTP work?  How about tracepath <host>?

---

### Post by jonomayo on 2007-12-13
I believe you have the same problen as me...

Search how to disable ipv6 in firefox and do it.

If so firefox should then work but no other programme will be able to connect to the internet. The help you would then need is how to connect to the internet in other programmes which i would also be interested in...

Hope this is a slight help.

Jonathan

---

### Post by deelux523 on 2007-12-13
> **manthony121 said:**
> It is odd that you can 'ping' an external host, such as "www.google.com", but Firefox can't connect to it.  Can you ping other common sites ([www.ubuntu.com](www.ubuntu.com), etc)?  Does FTP work?  How about tracepath <host>?

Manthony 121-- 
I **can** ping other sites (Ubuntu.com, yahoo.com, etc)
I **cannot** connect to my FTP sites via FireFTP or via gFTP
Tracepath [www.ubuntu](www.ubuntu) .com  yields:

> 1:   192.168.1.100 (192.168.1.100)                                    0.785ms reached
       Resume:  pmtu 65535  hops 1  back 1 

Jonathan--
Given all the post-upgrade complaints I've read, I disabled IPV6 right after my upgrade was completed, so I'm afraid that should not be the issue.

Thank you both for your suggestions!

---

### Post by manthony121 on 2007-12-13
If you can ping external sites, then your network interfaces, routing, etc, is set up correctly, and the problem is with the applications.  Are you sure you have Firefox set for "direct connection to the Internet"?

Also, you should get more than one line in reply from a "tracepath" command.  Is what you have posted the entire trace?  When I "tracepath www.ubuntu.com", I get 16 hops before ending on "gw0-0-gr.canonical.com (91.189.88.10)"

---

### Post by deelux523 on 2007-12-14
> **manthony121 said:**
> If you can ping external sites, then your network interfaces, routing, etc, is set up correctly, and the problem is with the applications.  Are you sure you have Firefox set for "direct connection to the Internet"?

Also, you should get more than one line in reply from a "tracepath" command.  Is what you have posted the entire trace?  When I "tracepath www.ubuntu.com", I get 16 hops before ending on "gw0-0-gr.canonical.com (91.189.88.10)"

manthony121--
Thanks so much for your quick reply.

Thanks also for your explanation of the expected out put from Tracepath. Unfortunately, the trace listed above is the **entire** output of my trace, just one hop. I even tried agin this morning just to make sure. Still only one hop.

As for the "Direct Connection to Internet"--I am away from that machine for now, but will check that setting as soon as I can.

Thanks for all your help!
DL

---

### Post by dirkvic on 2007-12-14
As far as I can see, this is the same problem I am struggeling with. The output of my "tracepath www.ubuntu.com" is as follows:
```
sigmund@familie-pc:~$ tracepath www.ubuntu.com
 1:  familie-pc.local (192.168.1.6)                         0.140ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.339ms 
 2:  1.81-166-84.customer.lyse.net (81.166.84.1)            2.502ms 
 3:  129.84-234-175.customer.lyse.net (84.234.175.129)      2.115ms 
 4:  141.213-167-114.customer.lyse.net (213.167.114.141)    2.537ms 
 5:  no reply
 6:  ge-6-17.car1.Amsterdam1.Level3.net (213.244.165.237) asymm  7  31.976ms 
 7:  ae-32-54.ebr2.Amsterdam1.Level3.net (4.68.120.126)    39.328ms 
 8:  ae-2.ebr2.London1.Level3.net (4.69.132.133)          asymm 11  39.326ms 
 9:  ae-1-100.ebr1.London1.Level3.net (4.69.132.117)      asymm 11  46.675ms 
10:  ae-2.ebr2.London2.Level3.net (4.69.132.145)          asymm 12  39.702ms 
11:  ae-26-54.car2.London2.Level3.net (4.68.117.112)      asymm 13  40.145ms 
12:  195.50.121.2 (195.50.121.2)                          asymm 15  40.345ms 
13:  gw0-0-gr.canonical.com (91.189.88.10)                asymm 15  39.838ms 
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500
```

I have also tried wget. And it gets as far as this, and waits for a min or two and then times out:
```
--13:29:47--  http://vg.no/
           => `index.html'
Resolving vg.no... 193.69.165.21
Connecting to vg.no|193.69.165.21|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.vg.no/ [following]
--13:29:47--  http://www.vg.no/
           => `index.html'
Resolving www.vg.no... 193.69.165.21
Reusing existing connection to vg.no:80.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

--13:31:00--  http://www.vg.no/
  (try: 2) => `index.html'
Connecting to www.vg.no|193.69.165.21|:80... connected.
HTTP request sent, awaiting response... 
```

I am on a fujitsu siemens laptop esprimo v5535.

---

### Post by dirkvic on 2007-12-14
I found these errormessages in /var/log/cups/error_log:
```
E [14/Dec/2007:13:19:46 +0100] Unable to find IP address for server name "familie-pc"!
E [14/Dec/2007:13:19:46 +0100] Unable to open listen socket for address ::1:631 - Address family not supported by protocol.
```
These seems related to the problems since they are generated every time I do a wget.

Anyone know how to resolve this?

---

### Post by dave37 on 2007-12-14
I ran across a similar problem on my file server running dapper.  I could browse my lan, ping numerical ip addresses but not named.  If I added the first address of my router (192.XXX.X.1) as a DNS server in "network properties" everything worked fine.  If I run Gutsy from the LiveCD I have to change network from "roaming" to "dhcp" and then it works.

---

### Post by deelux523 on 2007-12-18
Sorry for my delay in response.


> **manthony121 said:**
> If you can ping external sites, then your network interfaces, routing, etc, is set up correctly, and the problem is with the applications.  Are you sure you have Firefox set for "direct connection to the Internet"?

manthony121--
Yep, my Firefox prefs are set as "direct connection to the internet." But mmy issues are not limited to Firefox, I cannot get updates from the repositories via update manager either.

> I ran across a similar problem on my file server running dapper. I could browse my lan, ping numerical ip addresses but not named. If I added the first address of my router (192.XXX.X.1) as a DNS server in "network properties" everything worked fine. If I run Gutsy from the LiveCD I have to change network from "roaming" to "dhcp" and then it works. 

dave37--
I have always had my router address listed as a DNS in my manual network settings, so unfortunately that's not it either.

Thanks alll for the suggestions. Can anyone reccomend any additional diagnostics I can run that would offer more insight? THANK YOU!

DL

---

### Post by dirkvic on 2007-12-19
I haven't gotten the wired up and running yet, I still have this problem. But I got the wireless up, and I am basicly content with that for now.

I manually removed ndiswrapper, then buildt it and installed it with the package from sourceforge (used another machine and USB memory stick). There are several threads on this forum describing it, but the instructions at sourceforge works just as good.

---

### Post by klapczuk on 2007-12-19
Hi,

I believe you have the same problem as mine - see my thread: 
[http://ubuntuforums.org/showthread.php?t=644629](http://ubuntuforums.org/showthread.php?t=644629)

Can you check - if it is not the problem at the ubuntu/router edge. In my case, everything works well with different router (of course this is not a solution). 
Can you confirm that you have stable TCP session to router (using for example  telnet or http)?

Best regards,

Krzysztof

---

### Post by deelux523 on 2007-12-20
Kryzstof,

THank you for your thoughts. I took a look at your thread, and it appears our problems are a bit different. Trying to connect via a Live CD was a great idea, though.

I **connected successfully **using an old Dapper Live CD. Unfortunately, I could not see any obvious differences in the config the CD created vs. what I have set up myself on the Gutsy desktop.

My other PC conects successfully from both WinXP and Ubuntu Gutsy, plus my gutsy desktop used to work--It just stopped recently, so my issues shouldn't be hardware related

Can anyone reccomend what diagnostics (ifconfig and what else?) I should run to compare **ALL the networking settings** between the Live CD operation and my regular boot?

Also, is there a way to delete all of the existing network settings and re-run the wizard-style configuration tool that works so well from the install disks?

THANKS EVERYONE!!
DL

---

### Post by gilf on 2007-12-21
You might find this useful if you haven't seen it already, with regard to the LiveCD and /etc/network/interfaces

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

Also you may want to add additional DNS entries into your network manager. Here's the site for a couple of useable open DNS addresses:

[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

hope this helps

---

### Post by deelux523 on 2007-12-26
Gilf,

Thank you for your insights. Your documentation is extraordinarily clear and well written, and was a valuable lesson to a relative noob like me.

As it turned out, I ran my old Dapper LiveCD to get access to the internet, downloaded and burned a Gutsy Live CD and performed a fresh reinstall, and WHAMMO! I'm connected again.

Because I had my */home *folder on an external drive, many of  my settings were preserved. I'll finish updating my Samba config tonight, and I should be in better shape than I was before all this happened.

**ADVICE FOR THE NOOBS (me included)**: ALWAYS have a Live CD of your current Ubuntu version handy, even if you used the Update Manager to upgrade from one version to the next. That way you can reinstall easily should you somehow blow something up. Having */home *on a different drive than the OS is pretty handy, too.  Here's a post on moving /home elsewhere,  [[http://ubuntuforums.org/showthread.php?t=46866]([http://ubuntuforums.org/showthread.php?t=46866).

Big thanks to all for your thoughts and help, and Happy New Year to everyone on the Gregorian calendar!

DL

---

