---
title: "Can not connect to devices on LAN. WAN connections are working normally."
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Bill Garneau on 2008-11-03
I can get out to the internet just fine, but I can not ping, SMB, RDP, or VNC to anything on my local LAN. I've been having a lot of trouble with my network connections since upgrading to 8.10 and I suspect I screwed something up in my attempts at fixing those problems.

Current routing table:
bgarneau@bgarneau-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.254.0   *               255.255.255.0   U     0      0        0 eth0
default         192.168.254.254 0.0.0.0         UG    0      0        0 eth0


192.168.254.0 is the correct network but I am getting destination unreachable trying to ping any device on this network.

---

### Post by puppywhacker on 2008-11-03
routing table looks short and fine. not much wrong there. I bet it's a firewall thing, take a look at shorewall, or directly to the netfilter

iptables -L -v

Otherwise you might want to make some network traces, to see which packets go out, and which come in.
tcpdump -i eth0 -s 1600 -v

goodluck

---

### Post by rkrizan on 2008-11-03
I'm having the exact same issue. I can't ping, ssh, ftp, telnet, nothing in or out of any computer on my network, to each other. Outgoing works just fine, to anything outside my network, But inside my network, it's all dead.

Please, if you find an answer to this problem, email me at rkclads AT gmail.com

Thank you

---

### Post by Bill Garneau on 2008-11-03
ding ding. Disabled moblock and everything is well again.

---

### Post by rkrizan on 2008-11-03
Damn. I don't believe I have moblock installed. I checked, couldn't find any service or package. I can ping my Ubuntu boxes from a WINDOWS machine no problem. I can't ping anything from within my LAN from my Ubuntu boxes though. I can ping my router, and my webserver and whatnot just fine.


Anyone have any suggestions?

---

### Post by mrkenvesta on 2008-11-19
i have the same problem

can use the net just fine, can ping my router, my xp box can ping my intrepid box, but interpid can't ping xp


anyone manage to solve this?

---

### Post by IrishWristwatch on 2009-06-18
Has anyone found a solution to this problem?  This has been happening to me for about 2 weeks now.  The computer will respond fine for about an hour, before it disappears off the network.  

Internet works fine, and I'm still able to see the computer from the router (WRT54G w/ Tomato 1.25), but nothing is able to connect to computer from the LAN.

edit: Now here is the strange thing.  I am not able to ping the computer **_from_** other devices on the network, but when I do a ping with the computer **_to_** other devices it works just fine.  It's only when I want to connect to the computer that it doesn't work.

---

### Post by wy5r on 2009-11-02
I have somewhat of the same issue.  My network is 172.31.12.0/24 working over eth1 which has an assigned address of 172.31.12.160 and is a wireless connection.  I don't have a wired connection.  My gateway router is 172.31.12.1.  I can ping 2 out of 7 devices on the network.  All other pinged devices respond with 'No route to host'.  I have gone to each device on the network and pinged the other existing devices and there are no issues.  It is only my ubuntu 9.10 device.  BTW, I've had this issue since 9.04 and thought that 9.10 would fix it.  No such luck.  Here's my config:

kds@radio:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:03:23:62:3b:ef  
             inet addr:172.31.12.160  Bcast:172.31.12.255  Mask:255.255.255.0


kds@radio:~$ ip route
172.31.12.0/24 dev eth1  proto kernel  scope link  src 172.31.12.160  metric 2 
default via 172.31.12.1 dev eth1  proto static

2 other linux boxes, one running RHEL4 and the other RHEL5.  Both have the same exact listing for the ip route command except for the ip address assigned to the box.  Also, have another laptop running ubuntu 9.04 with wired interface only.  It does not have any issues.

kds/WY5R

---

