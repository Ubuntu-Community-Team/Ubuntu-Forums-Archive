---
title: "Call ifdown when laptop hibernates?"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by rrwo on 2006-10-24
How do I configure my laptop so that it calls ifdown for enabled network interfaces (esp. wireless) when I hibernate?

---

### Post by rrwo on 2006-10-31
SOLUTION: install the hibernate package so as to have the scripts in /etc/hibernate.  Then update the common.conf script where it turns off networking to include the wireless adapter.

---

