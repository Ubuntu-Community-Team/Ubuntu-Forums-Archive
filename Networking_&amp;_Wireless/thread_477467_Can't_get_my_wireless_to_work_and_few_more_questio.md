---
title: "Can't get my wireless to work and few more questions about it."
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by oliverb4ss on 2007-06-18
I installed 7.04 a few months ago but I never really needed WiFi until now.
I already did a search, couldn't find anything helpful to me.

What is roaming mode? I assume it's the mode where the computer detects any WiFi networs in range.

So, my computer detects my home network and asks for a key, when trying to connect to it. I have a WEP hex key (I know, it's not the safest, but it'll do for now) and after entering the key, my computer succesfully logs into to network.

Despite having a connection to the network (the icon in the notitification area tells that my connection is ~55%) I can't actually connect to anything or view any pages on the web.

What might be the problem?

ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:0B:CD:5B:90:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11912 (11.6 KiB)  TX bytes:6886 (6.7 KiB)

eth0      Link encap:Ethernet  HWaddr 00:17:08:2E:B5:99  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe2e:b599/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23564594 (22.4 MiB)  TX bytes:3378537 (3.2 MiB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112575 (109.9 KiB)  TX bytes:112575 (109.9 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-0B-CD-5B-90-77-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44611 errors:0 dropped:0 overruns:0 frame:3991
          TX packets:8051 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3979739 (3.7 MiB)  TX bytes:377536 (368.6 KiB)
          Interrupt:11 

Thanks in advance.

---

### Post by jhofmann on 2007-06-18
The fact that you see something from the modem on your computer screen means you have all the hardware working, and much of the software.

I wonder if you need a name server?  When you try to load a page, does the browser say it can't get the page, or does it say it can't find the page?  Try configuring a name server somewhere.

Hope this Helps,

Jim.

---

### Post by oliverb4ss on 2007-06-19
It says "Server not found, Firefox can'tfind the server at www.ubuntuforums.org"
That page is ofcourse displayed with any site, not just the forums.

Sorry, I'm not that computer-savvy to know how to configure or set up a name server. I'm not even sure what it is, for that matter.

So, is there any further advice for me?

---

### Post by bluetracer on 2007-06-19
Open up a console and type 'cat /etc/resolv.conf' (no quotes), then paste the output here.

A name server converts names like [www.google.com](www.google.com) into numerical IP addresses that the computer can connect to.  In order to view websites, your computer needs to know about a name server.  The file /etc/resolv.conf contains the numerical IP addresses of the name servers your computer knows about.  Normally these are assigned by DHCP (automatic configuration), but depending on your setup they might not be.  The contents of resolv.conf will tell us if this is your problem

---

### Post by oliverb4ss on 2007-06-20
The output of cat /etc/resolv.conf:

search lan
nameserver 192.168.1.254

I haven't had the chance to test any other wireless networks than my home one, but then again my dad's laptop can connect to it without problems, so I doubt it's a problem with the network itself.

---

### Post by conjur3r on 2007-06-20
The ifconfig output suggests that your wireless doesn't have an IP address.  The wireless may be *associated* with the access point but requires an ip address and other networking configuration to be able to use the network.

---

### Post by oliverb4ss on 2007-06-24
Okay, just out of the blue, my wireless started working, yay!!

Thanks anyway :)

---

