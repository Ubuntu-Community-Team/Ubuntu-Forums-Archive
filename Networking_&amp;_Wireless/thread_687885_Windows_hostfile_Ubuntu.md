---
title: "Windows: hostfile Ubuntu:???"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by dhtseany on 2008-02-04
Hi all,

This is probably a simple question, but I need to manually add a DNS entry under UB7.10.

I know under XP it's C:\Windows\System32\etc\Drivers\hostfile

Help!

Peace
Sean

---

### Post by croto on 2008-02-04
Hey, the file you're looking for is /etc/hosts

---

### Post by jetsam on 2008-02-04
It's at /etc/hosts

You can get all the details with **man hosts**, but basically just add the ip address, a tab, and the name to resolve under the entry "127.0.0.1     localhost".

---

