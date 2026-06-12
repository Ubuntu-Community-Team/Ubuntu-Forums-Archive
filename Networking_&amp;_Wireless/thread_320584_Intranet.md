---
title: "Intranet??"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by stormchas3r on 2006-12-17
I have a ubuntu 6.06 webserver serving externally.  What file do I need to edit to be able to connect to the webserver thru internal ip address and resolve it to the domain name internally?

ie.

192.168.1.1         webservername
localhost              webservername

I forget what file I need to edit to make this work.

Ty

---

### Post by bernied on 2006-12-17
If you've only got a few machines on the network then you just add an entry in /etc/hosts in linux or C:\Windows\System32\drivers\etc\lmhosts (or similar location, might have this a bit wrong) in Windows.

Otherwise you need your DNS to point at it - this might be your router.

---

