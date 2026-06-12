---
title: "Moving from a Tomato FW based router to an x86 router"
date: 2017-06-13
forum: Networking &amp; Wireless
---

### Post by marcin5 on 2017-06-13
Hi,


I'm in the process of upgrading my network.
Now it's time to change my current (Netgear R7000 with Tomato by Shibby FW) router to a x86 based router.
I do have an Asus RT-AC5300 that takes care of AP functions (which I switched off on my R7000), so the x86 machine wont be bothered with WiFi.

Here is a list of functions I use on my router (in addition to routing/firewall):
1. Some optware apps (they're all in the repos so it's only a matter of installing them and copying their config files)
2. PPPoE connection with my ISP
3. DDNS updates (I do have a static external IP, but I'm also in process of moving from a paid domain name to a free one - on no-ip.com)
4. DHCP server
5. Static MAC->IP (well multi MAC->IP as some devices have a cable and a WiFi connection and I want them to have the same IP no matter how they connect to the network)
6. Local DNS cache (this was done using dnsmasq on Tomato FW)
7. AdBlocking (done at the DNS level)
8. Some port forwarding
9. Local IP based access restrictions (to be exact one IP on my network has access restricted to some sites)
10. QoS (using port/IP based rules and a few also had L7 used)
11. OpenVPN server with TAP (I don't use TUN)
12. OpenSSH

I've tested some router/firewall x86 distros (unfotunatelly each one had some functions missing and/or turned off) and from those tests I'd like to also add some functions that are unavailable on Tomato FW.
Those are:
1. NTP server for my LAN
2. Transparent proxy
3. Update accelerator (for Linux and Windows updates)

I do plan to install munin for some monitoring of the machine, and also webmin to help me with the setup.
Is using webmin ok, or should I leave it alone and use console only based config?

Hardware specs that'll run this:
Mini-PC with Intel I5-5250U (2 cores/4 threads)
8GB RAM
128 GB SSD
1TB HDD
4 x Intel 1Gb NIC

I plan on adding a mSATA 4G modem to this machine in the future and setting it up as a fallback connection if my main connection fails. But that's a topic for a later date.

For now I've installed Ubuntu Server 16.04.2 LTS on that machine and I'm doing some stability tests.

I would greatly appreciate any help with making this work. I do know some networking basic etc. But I fear that when I'll try to make this config on my own I'll endup with a swiss cheese - full of holes. Hope that the networking gurus here in the forums will try to help.

Best regards
Szafran

---

### Post by TheFu on 2017-06-14
Sounds like you are headed in the right direction.

A few ideas:
* Ars Technica has a series of articles about building your own x86 router starting with Ubuntu Server. You might find that helpful.
* I wouldn't use any web-min type tool. It is just another attack vector. Usually, the people who need it aren't able to properly secure it.
* I'd load Ubuntu Server 16.04.1 LTS which had 5 yrs of support.  16.04.2 only has 12 months if you look at the prior release schedules for the .dot releases.  Don't do 'dist-upgrade' or you'll be pushed to the shorter supported release period in the upgrade.

The specifications you have would serve a medium-sized business.
A core i5 is overkill.
More than 4G of RAM is overkill.
An SSD is overkill and more than 16G of total storage is overkill.

Since you've selected to run a normal Ubuntu Server (excellent choice, IMHO), adding anything you like isn't hard.  NTPd is easy to add.

Might you consider a BSD-based router that runs on x86 HW?  Something like pfSense or OpenSense?  They have the FreeBSD stack, which is known to be the gold standard.  There are addons for pfsense for almost everything. Your HW can handle **all** of them. It has a web-gui and very easy backup/restore methods.  With the backup, it is trivial to perform a compete system upgrade (OS, HW, whatever), then restore and be 100% back.  All settings, addons, certs, whatever are handled.

I'm not certain I understand what an "update accelerator" means.  I run apt-cacher-ng, but not on my gateway.  It runs on the media server and all the systems point to that service in their apt settings.  My GW is a 10W x86 system with 4 cores, purpose built to be a router.

---

### Post by marcin5 on 2017-06-14
Thank you for the reply.
I've tried pfSense. Took me less than a minute after installing it to know that I wont be using it - I just checked if there is a way to get lcd4linux to run on it (there's not). And that's one of the basic apps that I use now (shows me my routers status on a 4x40 LCD).
Update accelerator is a cache for Windows and Linux update files - it's available on IPFire - I think it's a part of a proxy (at least one must enable proxy to enable the accelerator).
I'll take a look at those articles.

Any other good tutorials that can help me achieve my goals ?
A good one for configuring OVPN from scratch to make it work exactly like all the devices were on a single LAN no matter from where they are connecting would be nice. Also a config that'll work properly with Ubuntus Network Manager would be nice (with my current setup NM says that no config was sent from the server and disconnects - this config works from a command line).

EDIT: Is this what you had in mind: [https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) ? (I ask because this looks like a single article)

---

### Post by TheFu on 2017-06-15
I use system monitoring for routers with alarming, but to each their own.

Good tutorials?  help.ubuntu.com  They usually cover the simple situations, but allow for non-trivial configs too. There are pros and cons for most things.  Be cautious trying to extend your LAN as a single network. Allowing broadcast networking over a VPN has some issues for obvious reasons.

Just start by eating the elephant. 1 project at a time. Make backups along the way.  I've found to really understand a setup, I need to do it 3 times. 

Can't help with NM or much Windows for a variety of reasons. Sorry.

---

### Post by marcin5 on 2017-06-15
Thank you for the reply.

Hmm, I don't need help with Windows - didn't even know I asked for it. In fact I'm currently also in the process of moving every machine I can away from Windows.
I used this OVPN config with TAP for over 5 years now - works like a charm. But what worked fine with GUI on Windows doesn't work with NM on Ubuntu (and there is no current GUI software for Linux that works properly).

I've just loaded IPFire from backup and exported the config that I allready made there to help me with making the rules on the Ubuntu Server.
BTW I've measured and this machine takes ~20W under full load and about 5W in idle - so it should be ok for a router (since this is less than my current R7000 than I say it's ok :) )

As for update accelerator this is what I've found in some files on IPFire:
# This code is distributed under the terms of the GPL
#
# (c) 2006-2008 marco.s - [http://update-accelerator.advproxy.net](http://update-accelerator.advproxy.net)
#
# Portions (c) 2008 by dotzball - [http://www.blockouttraffic.de](http://www.blockouttraffic.de)
#
# dotzball 2008-05-27:
#               move functions from all local files to one library file
#
# $Id: updxlrator-lib.pl,v 1.1 2008/11/29 00:00:00 marco.s Exp $

and from what I've seen it's somehow connected with squid.

"system monitoring for routers with alarming" - can you be more specific ? Until now I've used some monitoring bash scripts that I wrote + adb + old Android phone to send SMS info messages.

---

### Post by TheFu on 2017-06-15
> 3. Update accelerator (for Linux and Windows updates)
I took that to be asking for something Windows-related. I also assumed you wanted Windows to work over the VPN, hence the comment about avoiding broadcast protocols with the VPN settings.

I use tun with my openvpn, so doubt I can be much help.  Tap performance was always poor, so avoiding it was important to me.

Sorry if I was off base. With 25+ yrs experience, I see all sorts of things that many people don't and often see complexities that might not be important .... or might be critical.

Nagios for alarming, but you can use whatever you like.

---

### Post by marcin5 on 2017-06-16
Ah I see.
Well it's a bit true. Although I'm moving all my machines to linux, I'm not the only one on my network. So some Windows machines will be present (I doubt that I could convince rest of the family to resign being on the dark side ;)).
I don't care much about TAP overhead - more important to me is that everything outside works exactly as inside (including Windows machines). Maybe some day I'll add a second OVPN server TUN connection when it becomes neccessary (right now on my R7000 I do have preconfigured a TUN server, but it's turned off).

Right now I've started a basic new router config. I do try to read up on all things and alternatives (currently on the dhcp/dns stage), but there's a LOT of those. For starters I think I'll stay to those things that are used on the Tomato FW and after getting all things working I'll be slowly analysing if theres some place for improvement that can be done on my config.

---

### Post by marcin5 on 2017-06-18
I have some thing allready working on the new config.

I came into a problem a can't seem to fix it.
I can't access my external ip from inside the network using my domain (it works fine when I connect from outside - eg. from my mobile connection).
I've tried a few things that I've found online but none helped.
Can you advise what to do ?

This is my current iptables:
```
# Generated by iptables-save v1.6.0 on Sun Jun 18 17:43:47 2017*mangle
:PREROUTING ACCEPT [18141261:17716921424]
:INPUT ACCEPT [67295:8500344]
:FORWARD ACCEPT [18072527:17708006514]
:OUTPUT ACCEPT [36942:3149130]
:POSTROUTING ACCEPT [18109469:17711155644]
-A FORWARD -o ppp0 -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1400:65495 -j TCPMSS --clamp-mss-to-pmtu
-A FORWARD -o ppp0 -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1400:65495 -j TCPMSS --clamp-mss-to-pmtu
COMMIT
# Completed on Sun Jun 18 17:43:47 2017
# Generated by iptables-save v1.6.0 on Sun Jun 18 17:43:47 2017
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [36942:3149130]
-A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -m state --state ESTABLISHED -j ACCEPT
-A INPUT -i lan0 -p tcp -m tcp --dport 53 -j ACCEPT
-A INPUT -i lan0 -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -i ppp0 -p tcp -m tcp --dport 64000 -j ACCEPT
-A INPUT -i lan0 -p tcp -m tcp --dport 64000 -j ACCEPT
-A INPUT -i lan0 -p udp -m udp --dport 67:68 -j ACCEPT
-A INPUT -i ppp0 -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -i ppp0 -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -j DROP
-A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i lan0 -o ppp0 -j ACCEPT
-A FORWARD -d 192.168.1.10/32 -p tcp -m tcp --dport 32400 -j ACCEPT
-A FORWARD -d 192.168.1.10/32 -p udp -m udp --dport 32400 -j ACCEPT
-A FORWARD -j DROP
COMMIT
# Completed on Sun Jun 18 17:43:47 2017
# Generated by iptables-save v1.6.0 on Sun Jun 18 17:43:47 2017
*nat
:PREROUTING ACCEPT [46204:4420483]
:INPUT ACCEPT [1311:89799]
:OUTPUT ACCEPT [31775:2274432]
:POSTROUTING ACCEPT [3:726]
-A PREROUTING -i ppp0 -p tcp -m tcp --dport 32400 -j DNAT --to-destination 192.168.1.10
-A PREROUTING -i ppp0 -p udp -m udp --dport 32400 -j DNAT --to-destination 192.168.1.10
-A POSTROUTING -o ppp0 -j MASQUERADE
COMMIT
# Completed on Sun Jun 18 17:43:47 2017
```

---

