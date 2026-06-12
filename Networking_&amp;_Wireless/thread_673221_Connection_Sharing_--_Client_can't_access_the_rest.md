---
title: "Connection Sharing -- Client can't access the rest of my internal network"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by Dromio on 2008-01-20
I have an xbox with xbmc in my living room. My main desktop PC (running Ubuntu) is also in my living room. My cable modem is far away upstairs, so my desktop PC uses a wireless card to connect to a wireless router upstairs.

I've run an ethernet cable from my desktop pc to my xbox. My desktop PC contains most of the videos I play on the xbox, so the ethernet cable makes it nice and fast. My setup is now like this:

router -> ath0 -> ubuntu -> eth0 -> xbmc

My home network is on 192.168.0.x. The router hands out addresses in this space. I set up my eth0 with the address 192.168.1.1. Then I set up xbmc to use a static ip of 192.168.1.2 with a gateway IP of 192.168.1.1 and a dns server at 192.168.0.1. 

I set up a script that runs the following iptables:
[INDENT]code:
$IPTABLES -t nat -A POSTROUTING -o ath0 -j MASQUERADE
$IPTABLES -A FORWARD -i ath0 -m state --state RELATED,ESTABLISHED -j ACCEPT
[/INDENT] XBMC is able to connect to the internet and read files from my desktop pc.

BUT, it's not able to read files from other machines on my network (most importantly my music server, 192.168.0.100). So it cannot access addresses in my router's ip range.

How do I allow it to get to those? I expect I have to add some sort of routing information in the desktop PC, but I have no idea how.

---

### Post by ICberg7 on 2008-01-30
You should to set up the xbmc to use 192.168.1.1 as your dns server, because it's inside the network. You can use bind9 (sudo apt get install bind9) and modify named.conf.options to include forwarders that go outside your network.

I'd also recommend looking at [http://help.ubuntu.com/community/InternetConnectionSharing](http://help.ubuntu.com/community/InternetConnectionSharing) for some info on this, but also take a look at the ongoing post at [http://ubuntuforums.org/showthread.php?p=4240102#post4240102](http://ubuntuforums.org/showthread.php?p=4240102#post4240102), as I've made some recommended changes.

Hope this helps.

---

