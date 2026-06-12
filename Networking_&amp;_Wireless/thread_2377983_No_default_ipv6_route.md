---
title: "No default ipv6 route?"
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by dankegel on 2017-11-18
My ISP supports ipv6, and the cable modem's admin
web interface can ping ipv6 addresses fine, so I was
surprised when I ran into delays doing apt-get on a
freshly installed ubuntu 17.04.  Rather than force ipv4
for apt as I had done in the past, I decided to tough it
out and try to get ipv6 working.

As it turns out, all I had to do was the single command

sudo ip -6 route add default via fe80::921a:dead:beef:foob dev enp4s0

(where  fe80::921a:dead:beef:foob is the address of my router).

After that, [http://ipv6-test.com/](http://ipv6-test.com/) reports things are working (but only scores 16/20, guess it couldn't look up my hostname, etc.)
and google searching via [http://ipv6.google.com](http://ipv6.google.com) works.

So... who's at fault here?   Surely users are not expected to issue that command.
I'm happy to report a bug via ubuntu-bug, but against what?
And what logs should I include?

---

