---
title: "IPv6 w/ Go6 + apache?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by im_an_alien on 2008-07-29
Yeah, so I've been running apache on my computer, hosting a website for a while now.  But I just got go6 set up on my router, and am now browsing the (3 or so pages of) IPv6 internet.  Everything's working fine, but now I want to set up an IPv6 site with apache.  I'm using [this](http://tldp.org/HOWTO/Linux+IPv6-HOWTO/hints-daemons-apache2..html) guide.  However, when I try to restart apache, I get this:
```
 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [2001:5c0:9f14:0:2e0:7dff:fe87:b7cf]:80
no listening sockets available, shutting down
Unable to open logs
```

So... is it even possible to host through a tunnel?  And if so, how can I fix this problem?

Also, this bit has been annoying me for a while now, but I haven't bothered to fix it:```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```How might I make that go away?

edit: Hold on, can I even host my IPv4 and IPv6 sites at the same time?

edit2: So, setting the port to 8080 fixed the problem.  But it is still not a total waste of a post.  I still have the ServerName thing, and I have a really weird problem as well.  I can't access my site(s) via loopback.  Typing "127.0.0.1" or "[::1]" into the address bar gives me a "The requested URL / was not found on this server." error, but by typing my local IP (or IPv6 IP) I can access my site.

---

