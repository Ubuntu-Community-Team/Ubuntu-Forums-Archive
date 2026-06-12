---
title: "PIng -a equivalent"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by jmasgalas on 2008-11-21
Is there a way to ping in Ubuntu the equivalent of MS ping -a? I mean to ping by IP and have the hostname returned.

---

### Post by Iowan on 2008-11-21
**ping -n** is the opposite - *prevents* looking up symbolic names for host addresses, but **man ping** doesn't show an option to lookup address and return hostname.

---

### Post by jmasgalas on 2008-11-24
Is there a utility I can install that has this capability?

---

