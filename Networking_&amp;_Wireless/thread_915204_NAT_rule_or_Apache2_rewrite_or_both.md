---
title: "NAT rule or Apache2 rewrite or both"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by dunno on 2008-09-09
Hi everyone,
Not sure if this is the right place to post this, but...

I have a hardy apache2 web server box, lets call it foo.bar.com.  Behind the web server is a Linksys SRW2008P switch (192.18.1.100, aliased 'switch') with it's own small web server.  Connected to the switch are 5 Linksys NSLU2s each with their own small web server.  The NSLU2s are accessible from inside the network using either an alias ('bob', 'mary', 'ted', 'alice', 'john') or their internal IP address (192.168.1.101 - 105).

Here's what I'd like to do:
I'd like to be able to access the web interface of both the switch and the NSLU2s from outside the network going thru the apache2 web server, as in:
[http://foo.bar.com/bob](http://foo.bar.com/bob), [http://foo.bar.com/mary](http://foo.bar.com/mary), [http://foo.bar.com/ted](http://foo.bar.com/ted), etc
and
[http://foo.bar.com/switch](http://foo.bar.com/switch)

Any helpful hints would be appreciated.
Thanks

---

