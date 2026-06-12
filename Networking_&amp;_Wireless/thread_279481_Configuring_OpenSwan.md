---
title: "Configuring OpenSwan"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by _Pete_ on 2006-10-18
Hello!

I would like to connect my two machines together using OpenSwan.
I have read the OpenSwan documentation and Wiki but things are still not opened for me.

Both machines have public ip-address and also virtualinterface which is used for local networking.

What I don't yet understand what the left, leftsubnet and leftnexthope means... So if you there are some Ubuntu specific instructions available I would be glad to see them.

br,

Pete

---

### Post by jbaloul on 2006-11-19
hope this helps...

[http://howtoforums.net/viewtopic.php?t=92](http://howtoforums.net/viewtopic.php?t=92)

JB

---

### Post by jmflyer on 2007-11-19
left=Your main site
leftnexthop=  (defaults to %direct - which means that it goes direct to the right side.  You could put %defaultroute which would use your default route instead of direct.  Be sure to define the routes if you use this)
leftsubnet=the internal subnet of your main site



Right=The Remote Site
(everything else the same as on the left.

On the wiki I think it's pretty well documented.  Maybe you weren't looking at the correct section of the WIKI?  (openswan to openswan)
[http://wiki.openswan.org/index.php/Openswan/Configure]("http://wiki.openswan.org/index.php/Openswan/Configure")

I followed this using Ubuntu Dapper almost bit for bit, and it worked.  The only thing I had to do was add 'Version 2.0' to the top of ipsec.conf.  Also something to note is that in ipsec.conf, an empty line means end of section.

---

