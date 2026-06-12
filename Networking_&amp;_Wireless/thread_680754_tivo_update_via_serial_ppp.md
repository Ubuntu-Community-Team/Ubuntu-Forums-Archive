---
title: "tivo update via serial ppp"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by jdratlif on 2008-01-28
I decided to try out Kubuntu and switch from gentoo. 

[http://gentoo-wiki.com/HOWTO_Tivo_PPP_Gateway](http://gentoo-wiki.com/HOWTO_Tivo_PPP_Gateway)

This page tells me how to setup the PPP link in gentoo. If I start pppd myself manually, I can tell Tivo to make a daily call immediately, and it works great.

However, in gentoo, I could start /etc/init.d/net.ppp0 and the pppd link would start up whenever Tivo tried to call. How can I make this automatic in Kubuntu?

I think I found a solution:

Make a tivo ppp script
/etc/ppp/peers/tivo

/dev/ttyS0
115200
debug
proxyarp
nocrtscts
local
noauth
xonxoff
192.168.1.2:192.168.1.6
persist
maxfail 0

sudo pon tivo

Add "pon tivo" to /etc/rc.local
Also add net.ipv4.ip_forward=1 in /etc/sysctl.conf and as root, echo "1" > /proc/sys/net/ipv4/ip_forward
I couldn't sudo that echo. I had to sudo /bin/bash, then do the echo as root, but maybe I messed up the command.

**edit 2**: The first one didn't work. Now I've added the maxfail option. I hope this will solve things. I'll edit again in a couple days.

**edit 3**: the maxfail thing was what I needed. Tivo has been updating perfectly for days.

**edit 4**: I am trying out Xubuntu now. I forgot to mention the ip forwarding part before.

---

