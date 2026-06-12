---
title: "DNSSEC validation failed: failed-auxiliary"
date: 2017-03-27
forum: Networking &amp; Wireless
---

### Post by 3togo on 2017-03-27
I can't browse google.com.hk but why?

jc@jc-T5400:~$ systemd-resolve google.com.hk
google.com.hk: resolve call failed: DNSSEC validation failed: failed-auxiliary
jc@jc-T5400:~$ systemd-resolve google.com
google.com: 172.217.24.46

-- Information acquired via protocol DNS in 55.4ms.
-- Data is authenticated: no

---

### Post by 3togo on 2017-03-27
I fixed the problem by setting DNSSEC to no in /etc/systemd/resolved.conf followed by

>sudo service systemd-resolved restart

but, setting dnssec to no is not a good idea, isn't it?

---

