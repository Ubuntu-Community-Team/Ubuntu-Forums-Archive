---
title: "NFS Lan and Wifi internet conflict"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by EnterDaMatrix on 2007-03-04
My setup is like this:

At our house we have a wireless network that I use to connect to the internet. I set up a little NFS server running Ubuntu and to make speeds as quick as possible it sits in my corner where it is sent through a Linksys router on my bookshelf which is plugged into my main PC. The problem is that when I'm connected to the LAN, I can't access the internet through my Wifi, even though network-manager says it's connected. I think that Ubuntu specifies one interface that it uses for the internet and locks out the other one. How can I tell it to use Wifi for internet and Lan for the server? Thanks.

---

### Post by georgeh on 2007-03-09
I had the same problem as you did.  Look at the following post:
[http://www.ubuntuforums.org/search.php?searchid=15948896](http://www.ubuntuforums.org/search.php?searchid=15948896)
I had it resolved by the many helpful people here.

---

### Post by georgeh on 2007-03-09
I had the same problem as you did. Except i was not dealing with wifi. But that shouldn't matter the solution should be the same.  Look at the following post:
[http://www.ubuntuforums.org/search.php?searchid=15948896](http://www.ubuntuforums.org/search.php?searchid=15948896)

---

### Post by Mr. C. on 2007-03-09
You likely have two default routes.  Please show output from:

ifconfig -a
netstat -rn

MrC

---

