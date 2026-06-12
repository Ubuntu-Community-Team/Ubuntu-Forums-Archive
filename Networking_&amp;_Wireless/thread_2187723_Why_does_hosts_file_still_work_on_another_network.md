---
title: "Why does hosts file still work on another network?"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by vayu on 2013-11-13
I moved my computers from a network based on 10.0.0.x to one based on 192.168.1.x.  I had my hosts file set to give names to the computers and to apache virtual hosts.  After moving the computers to this new network with different addresses, the names are still working.  The computer named at 10.0.0.20 can still be referred to by name, so can the local apache sites I've set up.  The network is now 192.168, but the hosts file names everything 10.0.  Why does this work?  I thought maybe something is ignoring the hosts file, but I was able to set a staging server to an offsite IP address in the same hosts file and that works.

I want to add and change some entries and I don't know what to do.  I suppose I should go to all the computers hosts files and set them properly, but this is a temporary network, I have a lot of computers, and scripts with a lot of entries.  Why is the current hosts file working? How is the name getting resolved to the new IP address when the hosts file gave it a different one?

---

