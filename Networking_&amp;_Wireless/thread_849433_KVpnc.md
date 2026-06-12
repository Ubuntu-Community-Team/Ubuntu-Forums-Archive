---
title: "KVpnc"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by colossuslinux on 2008-07-04
Okay, bear with me.  I have used linux in the past, but have always had someone around to help me out.  Now, I'm trying to make the switch and I'm on my own here.

I have a dell latitude D830 laptop that I've installed with Ubuntu 7.10.  I have most of the features working, but I'm having trouble with a VPN connection.  I am using KVpnc and I am finally able to get the connection established, but I can not connect to any point outside the local network.  I have tried pinging IP's for google, yahoo and even the ip for the ubuntu home page, but I'm still not getting anywhere.  I can ping the default gateway, but I can't ping any of the DNS servers.  When I use "#ping -c 4 google.com"  I get the response "ping: unknown host google.com"  but when I ping the ip directly I get "connect: Network is unreachable"  is there anyone out there who can help me with this issue?  I'm trying and I'm getting better, but I feel I still have a long way to go to master the arts of Linux... A LONG FREAKIN' WAY!!!

C-LOS

---

### Post by colossuslinux on 2008-07-05
I found a solution at [http://brian.pontarelli.com/2007/06/19/ubuntu-vpn-issues/](http://brian.pontarelli.com/2007/06/19/ubuntu-vpn-issues/)

I haven't implemented the full solution from that page, but simply using the command below worked.

"# sudo route add default gw 192.168.80.xxx"

the problem with the configuration of my VPN is that the gateway for my ppp0 connection needed to be set as the same as the ppp0's IP address.

Hope this can help someone else out there.

C-LOS

---

