---
title: "web access with vpnc"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Joe Momma on 2007-03-20
When I connect to my business vpn using vpnc, it drops my general internet connection.

I was wondering if there was a way I can send my ssh/scp/imap trafic through the vpn and still access webpages through my normal connection?

The workaround I have found right now is to ssh from my laptop to my desktop, and connect  the desktop to the vpn.  Then I have the internet from my laptop, and I have access to my business network by ssh-ing my desktop and from there ssh-ing to my company computer.  But I was thinking there must be a way to do this directly with just one computer.

Any ideas?

---

### Post by Joe Momma on 2007-03-22
Well, nevermind, I figured it out, but if anyone is curious the answer is here:


[http://www.gentoo.org/doc/en/draft/vpnc-howto.xml](http://www.gentoo.org/doc/en/draft/vpnc-howto.xml)


Basically I had to set my default route back to 192.168.0.1 on eth1 (my router) and add a net route to the addresses I wanted to access at work through tun0 (VPN tunnel).  Now when I want to see the internet it takes the default route, but when I try to connect to an ip in my work network it knows to go through the tunnel.

---

