---
title: "Not able to connect to internet"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by madbawa on 2006-09-20
Hello,
I recently installed Ubuntu 6.06 LTS. However I am **unable to surf the web** using the bundled Firefox browser. I am using a broadband connection. 

Using the console, **I can ping yahoo.com**, I **can even telnet** to yahoo.com at port 80 and it fetches the index page. But I am unable to open any page in firefox. 

In order to get Firefox working, I turned OFF IPv6 support in Firefox (go to about:config and set network.dns.disableIPv6 to "true").

Now Firefox works.

I tried running something known as Network
Tools (collection of ping, netstat, traceroute, etc). The ping works, but **traceroute doesn't**. The output of 'route' command seems fine and
there's nothing untoward in dmesg logs also. 

Also, **GAIM just doesn't work**. And **the updates notifier cannot connect** to the internet either. I am posting a TCPDump of GAIM trying to login to Yahoo:

listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
18:17:20.677931 IP 192.168.1.2.32769 > mygateway1.ar7.domain:  44426+
AAAA? scs.msg.yahoo.com. (35)
18:17:20.695683 IP mygateway1.ar7.domain > 192.168.1.2.32769:  44426
1/1/0 CNAME[|domain]
18:17:20.707704 IP 192.168.1.2.32770 > mygateway1.ar7.domain:  18537+
PTR? 1.1.168.192.in-addr.arpa. (42)
18:17:20.709127 IP mygateway1.ar7.domain > 192.168.1.2.32770:  18537-
1/0/0 PTR[|domain]
18:17:20.719559 IP 192.168.1.2.32770 > mygateway1.ar7.domain:  14283+
PTR? 2.1.168.192.in-addr.arpa. (42)
18:17:20.896180 IP 192.168.1.2.32771 > mygateway1.ar7.domain:  32384+
A? scs.msg.yahoo.com. (35)
18:17:20.898218 IP mygateway1.ar7.domain > 192.168.1.2.32771:  32384-
1/0/0 A 1.0.0.0 (51)
18:17:20.898636 IP 192.168.1.2.53570 > 1.0.0.0.5050: S
3350569277:3350569277(0) win 5840 <mss 1460,sackOK,timestamp 264741
0,nop,wscale 2>
18:17:23.897589 IP 192.168.1.2.53570 > 1.0.0.0.5050: S
3350569277:3350569277(0) win 5840 <mss 1460,sackOK,timestamp 267741
0,nop,wscale 2>
18:17:25.686425 arp who-has 192.168.1.2 tell mygateway1.ar7
18:17:25.686456 arp reply 192.168.1.2 is-at 00:04:76:de:7e:01 (oui
Unknown)
18:17:25.719330 IP 192.168.1.2.32770 > mygateway1.ar7.domain:  14283+
PTR? 2.1.168.192.in-addr.arpa. (42)
18:17:29.896679 IP 192.168.1.2.53570 > 1.0.0.0.5050: S
3350569277:3350569277(0) win 5840 <mss 1460,sackOK,timestamp 273741
0,nop,wscale 2>
18:17:30.737887 IP 192.168.1.2.32771 > mygateway1.ar7.domain:  32213+
PTR? 0.0.0.1.in-addr.arpa. (38 )
18:17:33.046786 IP mygateway1.ar7.domain > 192.168.1.2.32770:  14283
ServFail- 0/0/0 (42)
18:17:33.046839 IP 192.168.1.2 > mygateway1.ar7: ICMP 192.168.1.2 udp
port 32770 unreachable, length 78
18:17:35.737810 IP 192.168.1.2.32771 > mygateway1.ar7.domain:  32213+
PTR? 0.0.0.1.in-addr.arpa. (38 )
18:17:41.805193 IP mygateway1.ar7.domain > 192.168.1.2.32771:  32213
ServFail- 0/0/0 (38 )
18:17:41.805239 IP 192.168.1.2 > mygateway1.ar7: ICMP 192.168.1.2 udp
port 32771 unreachable, length 74 

Any ideas on what is to be done to get internet 'fully' working in Ubuntu? Also, I feel its quite sad that Ubuntu doesn't work out-of-the-box :(

---

### Post by Paul41 on 2006-09-20
You could try to disable IPv6 for everything since that worked for Firefox.

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by bastiegast on 2006-09-20
I had exactly the same problem, u should try specifieing the DNS servers provided by your ISP in /etc/resolv.conf or with  /etc/dhcp3/dhclient.conf

---

### Post by gumbald on 2006-09-20
Do you have a D-Link router by any chance? Fixed a problem like this last night. You need to find out your DNS from your IP and replace your router's address in /etc/resolv.conf and edit out one of the procedures in the other file mentioned. It's the "make_resolv_conf()" section. However, just found an Ubuntu archive which suggests a better method, take your pick: [http://www.ubuntuforums.org/archive/index.php/t-187466.html]("http://www.ubuntuforums.org/archive/index.php/t-187466.html")[http://www.ubuntuforums.org/archive/index.php/t-187466.html](http://www.ubuntuforums.org/archive/index.php/t-187466.html)

Apparently D-Link routers have problems forwarding DNS properly, not sure if a firmware update will fix it?

---

### Post by madbawa on 2006-09-22
Thanks for your replies. I will try each of the approaches and will post back what works. That way someone else having the same problem will not have to search a lot :)

---

### Post by madbawa on 2006-09-22
Ok. So I tried all the approaches mentioned above. Nothing worked :(

The point is that resolv.conf already had the correct nameserver in it. I guess that nameserver itself is screwed up. So I searched in these forums and found a page that lists all the DNS servers of various ISPs. I took one from a  NewZealand ISP and entered it in that dhclient.conf file (prepend nameservers). 

That got my GAIM working. I am online and chatting :) 

My experience with this ADSL stuff has been pretty shitty so far. Yes its a D-Link ADSL router and I have had my fights with D-Link's network cards as well earlier (had to modify a c file and compiled the driver).

So final step now is that I'll change my ISP.

Thanks again for your help guys.

---

