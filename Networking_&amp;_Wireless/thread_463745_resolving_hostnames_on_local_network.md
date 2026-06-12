---
title: "resolving hostnames on local network"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by vortmax on 2007-06-04
I have a small home network centered around a linksys WRT54G wireless router.  I have a file server running Fiesty hard wired into the router.

When I am running on windows, I can resolve the server by its host name, but when running fiesty on my laptop, it can't resolve the host names.  I can enter my router setup page and see that the router itself is resolving the server by its host name, so I'm gathering its a DNS issue.

Can I just add the IP of my router to my /etc/resolve.conf file or do I need to set up an official DNS on the server?

---

### Post by uteck on 2007-06-04
Yes, you can just add it to the /etc/resolve.conf file.  If you have multiple Linux box's you have to add it to all of them, or set up a DNS server, but for 1 box, this is the easiest way.

---

### Post by steeleyuk on 2007-06-04
> Yes, you can just add it to the /etc/resolve.conf file

that should be /etc/resolv.conf ;)

---

