---
title: "View network activity on other networked computers"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by supazio on 2008-03-18
Is it possible to track and view URLs accessed by computers on local networks?

---

### Post by nixscripter on 2008-03-19
Being the hacker that I am, I would suggest using the tcpdump utility, which captures packets, and read the HTTP protocol decode. Something like this in a terminal would do it: ```
sudo tcpdump -A -i any -s 0 port 80 | egrep -B 2 'GET.*HTTP'
``` It would look real messy, though. I suspect there is a utility that would let you do it much more cleanly, but I don't know what it would be.

---

