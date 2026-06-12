---
title: "simple dnsmasq question"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by nightfrost on 2007-12-26
Say I have a small home network with one server and two clients. The server runs dnsmasq and its /etc/hosts contains these lines (amongst others):

127.0.0.1 localhost
127.0.1.1 maincomputer
192.168.0.2 foo
192.168.0.3 bar

Further, let's say the computer 'foo' has received the correct ip number from the server, as has the computer 'bar'. Now, as far as I understand it should be possible for computer 'foo' to issue this command:

ping bar

with good results?

Have I completely misunderstood something here? Or do I need some special setting? Cause this isn't working for me.

Thanks a bunch!

---

