---
title: "SOS:A Big Network Configuration Problem in my case."
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by cnshzj007 on 2007-06-16
Backgroud:Dell D630 Intel965 IntelX3100 Ubuntu 7.04 installed yesterday Xserver failed 
I want to use safe model to apt-get update to solve the Xserver problem, but here comes the Title problem.

First I must change my MAC with these commands
         ifconfig eth0 down
         ifconfig eth0 hw ether 00:12:3F:02:A2:51
         ifconfig eth0 up

Secondly I must change the IP netmask and gateway with the codes
         ifconfig eth0 58.196.155.96 netmask 255.255.240.0
         route add default gw 55.196.144.1

Thirdly I must change the DNS like this
         vim /etc/resolve.conf
         add this
         nameserver 202.120.2.101

Then I check the network followed 
         ping -c 1 55.196.144.1 shows OK.
         ping -c [www.google.cn](www.google.cn) shows unknow host.

all of above is in the safemodel.

How can I figure it out?SOS:(

---

### Post by eks on 2007-06-16
Ouch. That looks a bit messy... 

But if you can ping a IP and not a domain, it should only be a DNS problem. You could see which DNS is configured in Ubuntu just by going to System/Administration/Network, but if you cannot start X then I dunno where you could find that information... sorry...

If you have X AND network broken, have you considered reinstalling everything from scartch?


eks

---

### Post by cnshzj007 on 2007-06-16
I just come back to DHCP network case.
Then apt-get update;apt-get dist-upgrade;apt-get install xserver-xorg-video-intel


then EVERYTHING is OK.

THK GOD!

---

