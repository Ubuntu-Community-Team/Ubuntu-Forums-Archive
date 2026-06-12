---
title: "Accessing a web site"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by expatCM on 2011-01-06
I used to be able to access [http://apod.nasa.gov](http://apod.nasa.gov) without issue.  Then one fine day for no known reason it would not load.  I get a message saying that the server was reset or there was a different problem loading the page.

If I run traceroute I can reach the site but the last 10 hops do not give any information (so I do not actually confirm it resolves).   If I use a proxy ([http://www.freeproxyserver.ca/](http://www.freeproxyserver.ca/)) the site always loads.

I have a Debian server and that takes the Internet from an ADSL connection in bridge mode.

Is there any easy way of checking whether the problem is my server or something creative from my ISP? The only way I can think of would be to reconfigure my ADSL modem / router (so that it is not in bridge mode) and then connect up a PC directly and see what happens.

Can I do anything else?

---

### Post by TeoBigusGeekus on 2011-01-06
It loads perfectly fine here.
A great site to test the availability of other sites is this:
[http://www.downforeveryoneorjustme.com/]("http://www.downforeveryoneorjustme.com/")

---

### Post by expatCM on 2011-01-06
yes, but I think that is the point.  Since the site will load for me through a proxy browser I can see that it is there.  The problem is finding out if this is a problem with my server or a problem with my ISP ...  it has to be one or the other....

---

### Post by sandyd on 2011-01-06
> **expatCM said:**
> yes, but I think that is the point.  Since the site will load for me through a proxy browser I can see that it is there.  The problem is finding out if this is a problem with my server or a problem with my ISP ...  it has to be one or the other....
in this situation, i would guess that theirs a router down (not your ISP) somewhere along the path to the server. Since the proxy usea a different IP address (and therefore a different location), it takes a different patch to the server, and is therefore unobstructed

---

