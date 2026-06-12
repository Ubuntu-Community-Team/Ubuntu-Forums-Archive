---
title: "Network Packeter"
date: 2019-06-10
forum: Networking &amp; Wireless
---

### Post by albert-redditt on 2019-06-10
How about someone modifying the kernel network packeter.

So all IP's other than 127 0 0 1 can only access a users home  \internet dir..

The internet dir would have:

\cookies
\webpages
\paswords
\webform completion
\downloads

Outside IP's could access the web browser .. to display audio and video..

Then you have a totally secure computer... 

You could have *.conf list of IP's  that can access the root login...

---

### Post by TheFu on 2019-06-10
Ah ... linux is multi-user. It is also a server, not just a desktop.  

Networking isn't connected to any specific userid on Unix systems.  Should 127.0.2.1 have local access? What about 127.5.243.1?

Ubuntu doesn't allow root logins by default, so that is handled already, unless an admin enables it.

Regardless, if you'd like to make the change and get it reviewed by the kernel team, convince them it is a great idea, have at it!  

In the meantime, perhaps you could use a cname + namespace tool to limit browser access to those places?  Check out firejail or snaps or [https://news.ycombinator.com/item?id=10030868](https://news.ycombinator.com/item?id=10030868) ... has some more options.  Lots of tools for you to check out which could meet your needs.

---

