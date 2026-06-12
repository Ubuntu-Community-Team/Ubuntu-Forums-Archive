---
title: "Reverse-IP Lookup"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by signul9 on 2008-04-04
Looking for a terminal based tool that performs a reverse IP lookup similar to reverseiplookup.net.  (Wanting to know list of domains hosted on IP.)

example - [http://www.reverseiplookup.net/?s=ubuntuforums.org&submit=Lookup](http://www.reverseiplookup.net/?s=ubuntuforums.org&submit=Lookup)

Tried dig -x, tried nslookup....  Can't get the amount of detail the web based version provides.

---

### Post by signul9 on 2008-04-04
[UPDATE]

Figured out a jank way using wget....

wget [www.reverseiplookup.net/?s=XXXDOMAINXXXX](www.reverseiplookup.net/?s=XXXDOMAINXXXX)

Suppose I could do an alias to simplify....  but still hopeful there's a command line tool already avail...

---

