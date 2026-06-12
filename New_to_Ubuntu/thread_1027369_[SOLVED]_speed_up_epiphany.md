---
title: "[SOLVED] speed up epiphany"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by som1special2 on 2009-01-01
any one know how to speed up epiphany?

---

### Post by mejy on 2009-01-01
It depends on which version of XUbuntu you're using.  Personally, I'd give Firefox 3.1 beta 2 and midori a go - depending on your hardware, one or both of those could be noticeably faster (one uses a more recent version of the gecko engine, the other webkit).  If there's some aspect besides page rendering that's too slow for you, you'll have to post more details for a more comprehensive answer.

---

### Post by linux_tech on 2009-01-01
in browser addr bar type:
about:config
scroll to 

right click on, then select toggle to change from

network.dns.disableIPV6 --false

to this:

network.dns.disableIPV6 --chng to --true

next scroll to these and check/change these settings to the following:
network.http.pipelining --chng to --true
network.http.proxy.pipelining --chng to -- true
network.http.proxy.pipelining.maxrequests --chng to 30.

---

