---
title: "need help with interweb"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by conspiracy_guy99 on 2006-08-31
ok, so i put Kubuntu on my system, and i cant get the internet to connect, on Window$ i had cox high speed and i was on a LAN, but i cant connect to the LAN or my ISP, i need help.....lots of help.....like a click-by-click guide here

---

### Post by briguy on 2006-08-31
For the most part, Kubuntu / Ubuntu should connect to the interweb on boot.  Are you hooked up using wired or wireless?  What have you tried to connect with (I'm assuming you've tried to browse with Konqueror).

---

### Post by conspiracy_guy99 on 2006-08-31
yeah, im wired, and yes, ive tried konqueror already, and it doesnt connect

---

### Post by sebastfr on 2006-09-01
a few tests you should try:

~> ping [www.google.com](www.google.com)

does this work? if not, you don't have any network connectivity (or no dns resolution).

also give us the output of the following commands:

~> ifconfig

and:

~> route

and:

~> cat /etc/resolv.conf

Then it might be easier to understand why you can't get internet.... good luck!

Seb

---

