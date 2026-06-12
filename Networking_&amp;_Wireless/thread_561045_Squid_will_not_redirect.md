---
title: "Squid will not redirect"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by chinleybrewer on 2007-09-27
Hello all, I am quite new to Linux - (well have played before but years ago).  I have installed Ubuntu FeistyFawn and been very impressed with how smoothly it went.

I am trying to setup a server which will filter web requests (for our local community association).  The machine is connected to the web via eth0 and has a second card eth1 for local network - eth1 has DHCP server.  This all works fine.

I have got Squid 2.6 installed and SquidGuard too.  After problems with owenership and permissions, I now have SquidGuard working (confirmed that it will block sites I have listed using the echo command-line test).  I have configured Squid as transparent (so that I do not have to set proxy settings on LAN connected browsers) and I can access the web via the LAN without having to configure proxy settings in my browser.

The problem I have is that I cannot seem to get Squid to redirect requests to SquidGuard:-k
Initially the instructions I used specified that I should use "redirect_program" in squid.conf but I have since found that Squid 2.6 seems to have changed that to "url_rewrite_program" but still it will not redirect, I can still access everything on the web from a machine connected on the LAN.

One thing I find strange is that /var/log/squid/access.log is not being written to.  Perhaps I have logging turned off somehow.

I started with this ([http://linuxgazette.net/141/lazar.html](http://linuxgazette.net/141/lazar.html)) tutorial and it has been great.  I have configured most things using Webmin and sometimes command line too.
Having searched and searched on the web, I am now stuck.  Does anyone have any idea how I can check why Squid will not redirect? - Is there some way I can check my Squid configuration?

Thanks for any suggestions you can offer...
Martin

---

### Post by chinleybrewer on 2007-09-27
Don't worry - fixed it at last!!

It turned out that I needed another rule in the shorewall firewall as follows:
Accept      Firewall     net    tcp    www

After much head scratching I added that rule and everything works as expected - superb!

---

