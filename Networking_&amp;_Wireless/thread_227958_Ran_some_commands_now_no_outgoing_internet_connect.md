---
title: "Ran some commands now no outgoing internet connection"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by skorpi0wn on 2006-08-02
I have been installing and removing some software using aptitude.  My three most recent commands:

aptitude install xterm  -> Successful
aptitude remove xterm -> Successful
aptitude clean -> Successful

Now I just tried to run
aptitude update and I get the response:

Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Temporary failure resolving 'packages.freecontrib.org'
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Temporary failure resolving 'archive.canonical.com'

and so on...

Then I noticed that nothing outbound works.  I can't ping, use lynx, or do anything with an outbound connection.  I am however able to connect to the server through port 22 using SSH. It will also host web pages using Apache through port 80.

Any idea on how I can fix this remotely?

Thanks for any help in advance.

UPDATE:  I noticed that I can actually access ip addresses.  So, I'm guessing that I screwed up something with the nameserver.  I added the router's IP to /etc/resolv.conf  Worked great!  Thanks!

---

