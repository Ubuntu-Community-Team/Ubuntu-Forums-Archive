---
title: "Partially working internet"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by Karris on 2006-11-14
First off, hello everyone, all fresh ubuntu user here! Have some experience with debian linux some years ago, and decided to give it a go again, and fell over the new ubuntu, which seemed nice! I dual booted my comp with a new edgy ubuntu installation, tweaked most of the stuff so it fit my pc as it should...all except one thing: The internet.

I'm on a LAN with a router acting as a dhcp server. It's in my building-wide so I don't have access to the router, and I can't figure out who is administratoring the damn thing. Strange thing is, I can access some sites, like [www.google.com](www.google.com), or [www.atari.com](www.atari.com), but not other sites like [www.ubuntu.org](www.ubuntu.org), [www.linux.org](www.linux.org). The browser says "looking up [domain]...connecting to [domain]...connected to [domain]...waiting on [domain], and then it just hangs there forever, with no progress. I can't ping these not-working sites either.

I'm really not sure what might cause that, but I've been reading these forums the last few days, trying this and that, including disabling ipv6, switching back and forth with DNS addresses (Tried OpenDNS as well), but nothing is working.

The internet on my winXP64 partition is working fine, and with the ubuntu easy-to-use dhcp server auto config, shouldn't it be working as well in linux?

So...any help will be appreciated! ](*,)

---

### Post by Karris on 2006-11-16
Still got this problem. I've noticed that both on the GUI networking interface and when running ifconfig, it states that I have a lot of "recieving errors", the number increasing everytime I try to enter one of the websites I can't connect to, for some reason. I'm almost sure it's some stupid little thing I've forgot to take care of. 

I'll try later this evening or tomorrow to get some files posted, it's really begun to put me off :(

---

### Post by dataw0lf on 2006-11-16
Can you supply relevant tcpdump output?

---

### Post by Karris on 2006-11-16
Not exactly sure what relevant means, if you get my point, hehe. But I started tcpdump, and ran a small test where I first tried to connect to linux.com, ubuntu.org, neither of which worked. Here is the output:

listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
20:27:20.649137 IPX 00000000.00:c0:9f:9c:72:70.0453 > 00000000.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 2639538687/1.2
20:27:20.695087 IP 192.168.1.36.32773 > 192.168.1.1.domain:  63229+ A? www.linux.com. (31)
20:27:20.696001 IP 192.168.1.36.32774 > 192.168.1.1.domain:  13678+ PTR? 1.1.168.192.in-addr.arpa. (42)
20:27:21.667027 IP 192.168.1.1.domain > 192.168.1.36.32773:  63229 1/5/5 A ostg.com (233)
20:27:21.667296 IP 192.168.1.36.59230 > ostg.com.www: S 1050175568:1050175568(0) win 5840 <mss 1460,sackOK,timestamp 13899 0,nop,wscale 2>
20:27:21.668380 IP 192.168.1.1.domain > 192.168.1.36.32774:  13678 NXDomain 0/1/0 (119)
20:27:21.668698 IP 192.168.1.1.domain > 192.168.1.36.32773:  63229 1/5/5 A ostg.com (233)
20:27:21.668727 IP 192.168.1.36.32774 > 192.168.1.1.domain:  63246+ PTR? 36.1.168.192.in-addr.arpa. (43)
20:27:21.668737 IP 192.168.1.36 > 192.168.1.1: ICMP 192.168.1.36 udp port 32773 unreachable, length 269
20:27:21.670449 IP 192.168.1.1.domain > 192.168.1.36.32774:  13678 NXDomain 0/1/0 (119)
20:27:22.747868 IP 192.168.1.1.domain > 192.168.1.36.32774:  63246 NXDomain 0/1/0 (120)
20:27:22.748354 IP 192.168.1.36.32774 > 192.168.1.1.domain:  27799+ PTR? 177.250.35.66.in-addr.arpa. (44)
20:27:22.749570 IP 192.168.1.1.domain > 192.168.1.36.32774:  63246 NXDomain 0/1/0 (120)
20:27:22.907060 IP ostg.com.www > 192.168.1.36.59230: S 2028790784:2028790784(0) ack 1050175569 win 5792 <mss 1460,sackOK,timestamp 2225367638 13899,nop,wscale 0>
20:27:22.907113 IP 192.168.1.36.59230 > ostg.com.www: . ack 1 win 1460 <nop,nop,timestamp 14209 2225367638>
20:27:22.907231 IP 192.168.1.36.59230 > ostg.com.www: P 1:408(407) ack 1 win 1460 <nop,nop,timestamp 14209 2225367638>
20:27:23.396497 arp who-has 192.168.1.1 (00:20:6f:1a:de:8d (oui Unknown)) tell 192.168.1.73
20:27:23.898266 IP 192.168.1.1.domain > 192.168.1.36.32774:  27799 2/2/2[|domain]
20:27:23.899068 IP 192.168.1.36.32774 > 192.168.1.1.domain:  37266+ PTR? 73.1.168.192.in-addr.arpa. (43)
20:27:23.900226 IP 192.168.1.1.domain > 192.168.1.36.32774:  27799 2/2/2[|domain]
20:27:24.146622 IP ostg.com.www > 192.168.1.36.59230: . ack 408 win 6432 <nop,nop,timestamp 2225367762 14209>
20:27:25.093283 IP 192.168.1.1.domain > 192.168.1.36.32774:  37266 NXDomain 0/1/0 (120)
20:27:25.094908 IP 192.168.1.1.domain > 192.168.1.36.32774:  37266 NXDomain 0/1/0 (120)
20:27:25.094937 IP 192.168.1.36 > 192.168.1.1: ICMP 192.168.1.36 udp port 32774 unreachable, length 156
20:27:32.616218 IP 192.168.1.36.59230 > ostg.com.www: F 408:408(0) ack 1 win 1460 <nop,nop,timestamp 16636 2225367762>
20:27:32.619208 IP 192.168.1.36.32774 > 192.168.1.1.domain:  745+ A? www.ubuntu.org. (32)
20:27:33.876394 IP 192.168.1.1.domain > 192.168.1.36.32774:  745 2/2/2 CNAME[|domain]
20:27:33.876831 IP 192.168.1.36.53134 > agoraserver.upc.es.www: S 1068769597:1068769597(0) win 5840 <mss 1460,sackOK,timestamp 16951 0,nop,wscale 2>
20:27:33.877095 IP 192.168.1.36.32774 > 192.168.1.1.domain:  50528+ PTR? 18.195.83.147.in-addr.arpa. (44)
20:27:33.950417 IP 192.168.1.1.domain > 192.168.1.36.32774:  745 2/8/6 CNAME[|domain]
20:27:34.034320 IP ostg.com.www > 192.168.1.36.59230: . ack 409 win 6432 <nop,nop,timestamp 2225368750 16636>
20:27:34.770718 IP 192.168.1.1.domain > 192.168.1.36.32774:  50528 1/2/2 (149)
20:27:34.834802 IP agoraserver.upc.es.www > 192.168.1.36.53134: S 1616795870:1616795870(0) ack 1068769598 win 5792 <mss 1460,sackOK,timestamp 2191381010 16951,nop,wscale 2>
20:27:34.834850 IP 192.168.1.36.53134 > agoraserver.upc.es.www: . ack 1 win 1460 <nop,nop,timestamp 17191 2191381010>
20:27:34.834972 IP 192.168.1.36.53134 > agoraserver.upc.es.www: P 1:409(408) ack 1 win 1460 <nop,nop,timestamp 17191 2191381010>
20:27:34.843457 IP 192.168.1.1.domain > 192.168.1.36.32774:  50528 1/2/1 (133)
20:27:34.843487 IP 192.168.1.36 > 192.168.1.1: ICMP 192.168.1.36 udp port 32774 unreachable, length 169
20:27:35.826511 IP agoraserver.upc.es.www > 192.168.1.36.53134: . ack 409 win 1716 <nop,nop,timestamp 2191381258 17191>
20:27:41.631803 IP mu-in-f104.google.com.www > 192.168.1.36.46627: F 2596242439:2596242439(0) ack 788116256 win 8190
20:27:41.632126 IP 192.168.1.36.32774 > 192.168.1.1.domain:  24003+ PTR? 104.135.85.209.in-addr.arpa. (45)
20:27:41.670907 IP 192.168.1.36.46627 > mu-in-f104.google.com.www: . ack 1 win 11440
20:27:42.318979 IP 192.168.1.36.53134 > agoraserver.upc.es.www: F 409:409(0) ack 1 win 1460 <nop,nop,timestamp 19062 2191381258>
20:27:42.321790 IP 192.168.1.36.46627 > mu-in-f104.google.com.www: F 1:1(0) ack 1 win 11440
20:27:42.321834 IP 192.168.1.36.46626 > mu-in-f104.google.com.www: P 795781326:795781826(500) ack 2771519724 win 34320
20:27:42.377192 IP 192.168.1.1.domain > 192.168.1.36.32774:  24003 1/4/4 (216)
20:27:42.378232 IP 192.168.1.1.domain > 192.168.1.36.32774:  24003 1/4/4 (216)
20:27:43.110685 IP mu-in-f104.google.com.www > 192.168.1.36.46627: . ack 2 win 8190
20:27:43.116134 IP mu-in-f104.google.com.www > 192.168.1.36.46626: . ack 500 win 6432
20:27:43.185104 IP agoraserver.upc.es.www > 192.168.1.36.53134: . ack 410 win 1716 <nop,nop,timestamp 2191383098 19062>
20:27:43.234003 IP mu-in-f104.google.com.www > 192.168.1.36.46626: . 1:1431(1430) ack 500 win 6432
20:27:43.234027 IP 192.168.1.36.46626 > mu-in-f104.google.com.www: . ack 1431 win 37180
20:27:43.234118 IP mu-in-f104.google.com.www > 192.168.1.36.46626: P 1431:2141(710) ack 500 win 6432
20:27:43.234129 IP 192.168.1.36.46626 > mu-in-f104.google.com.www: . ack 2141 win 37180
20:27:44.426234 IP 192.168.1.17.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
20:27:44.426513 IP 192.168.1.36.32774 > 192.168.1.1.domain:  42655+ PTR? 255.1.168.192.in-addr.arpa. (44)
20:27:45.175623 IP 192.168.1.17.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
20:27:45.599416 IP 192.168.1.1.domain > 192.168.1.36.32774:  42655 NXDomain 0/1/0 (121)
20:27:45.599681 IP 192.168.1.36.32774 > 192.168.1.1.domain:  13593+ PTR? 17.1.168.192.in-addr.arpa. (43)
20:27:45.602629 IP 192.168.1.1.domain > 192.168.1.36.32774:  42655 NXDomain 0/1/0 (121)
20:27:45.925649 IP 192.168.1.17.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
20:27:46.493504 IP 192.168.1.1.domain > 192.168.1.36.32774:  13593 NXDomain 0/1/0 (120)
20:27:46.497196 IP 192.168.1.1.domain > 192.168.1.36.32774:  13593 NXDomain 0/1/0 (120)
20:27:46.497218 IP 192.168.1.36 > 192.168.1.1: ICMP 192.168.1.36 udp port 32774 unreachable, length 156


Not sure which part of it is the culprit. I suspect it's something to do with the lines where it says "udp port 32774 unreachable", but since the net is working in windoze it should be able to connect in ubuntu as well.

---

### Post by tobiaseigen on 2006-11-16
Hi - 

Interesting.. I'm having a similar problem, also on Ubuntu 6.10. I can get to some websites, and not others. I can access [http://www.kabissa.org](http://www.kabissa.org) with no problems but [http://www.google.com](http://www.google.com) does not show up at all. When I do a traceroute to [www.google.com](www.google.com), It shows five hops and it hangs there with no reply. 

Generally the connection even on the sites that work is incredibly slow - and it takes forever to load pages that are fast on a windows machine on the same network. 

I am new to Ubuntu and new to using linux as a desktop machine - happy to provide troubleshooting info but need guidance. 

So far: 
- I'm using Qwest DSL with a DSL wireless modem
- I'm using DHCP
- Networking info is comparable to the windows machine and seems correct - though I am not familiar with some of the terminology (like host etc) 

Would be most grateful for any guidance. 

Thanks! 

Tobias

---

### Post by FrodoB on 2006-11-16
Almost sounds like your browser somehow. Have you both looked at disabling ipv6, see:

[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6)

---

### Post by Karris on 2006-11-17
Thanks for replying!

But yeah...I tried disabling ipv6, also stated that in the first post. It's not just the browser, I have troubles with apt-get as well. Tried disabling it both in the about:config of mozilla, and in the /modprobe/alias file.

Still to no avail :(

---

### Post by Karris on 2006-11-21
I'm about to be at my wits end...no matter what I do, I can't this accursed internet to work. I've begun to think that it's a hardware conflict or something, because I've disabled ipv6 systemwide, tried several DNSses, including that of my ISP, and tried taking a static IP instead of dynamic from the DHCP server, none of it is working...

I've found out that there is a connection through to -all- sites, they simply take so long to load that often, it times out.

](*,) ](*,) ](*,)

---

### Post by Karris on 2006-11-22
Woohoo! Solved it!

I found a fix, seeming with most SiS190 type integrated network chips.

What I did was:

```
sudo ifconfig eth0 mtu 1492

sudo /etc/init.d/networking restart
```

And that's it!

I can't say I know what I did technically, but it sure worked. :D

---

### Post by stream303 on 2006-11-23
Glad to see you got that fixed.  That mtu fix you wrote went right into my notebook.

If there are other lingering dns issues, you may want to see this:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

### Post by craiglarry on 2006-11-23
same in many ways for me, 64 bit, winxp working in double boot fine. At first the internet was great with ubuntu 64. Have double boot computers in two cities, diff service, but reaction the same. The longer it's on the worse it gets. It seems that 64 bit is just too new and too soon. Apparently not ready for prime time. Disappointing, really! I'm a newbie and if I could find a fix that I could understand I'd have a go at it. The worst situation is in email services surfing out of emails, but the problem exist to a degree in all situations. Reinstalled once already and that really helped, but can I reinstall every day to get a few hours of service? You all know that answer to that stupid idea. Have an idea that we're looking at installed stuff that never comes to the light of day and computer looking for it and not finding and getting confusing messages. I quit installing anything because of this possibility. Dont'know how to work around this 64 bit oddity.

---

