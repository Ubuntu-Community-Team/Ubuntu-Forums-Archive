---
title: "pdnsd doesn't bind"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by aladinonl on 2008-08-21
Hi,
I'm new to ubuntu. 
I'm trying pdnsd. pdnsd is in /etc/init.d but it doesn't automatically start. When i try to start it manually by $ sudo pdnsd, i get:
* 08/22 08:39:25| pdnsd: error: Could not bind tcp socket: Address already in use
* 08/22 08:39:25| pdnsd: error: Could not bind to udp socket: Address already in use
* 08/22 08:39:25| pdnsd: error: tcp and udp initialization failed. Exiting.
No pdnsd whatsoever is active.

However, when i try dig some domain, it appears "unbelievably" fast. $ dig google.com (and all other domains i tried), the result is like this:
;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Aug 22 09:34:46 2008
;; MSG SIZE  rcvd: 36

any help?
thanks.

---

