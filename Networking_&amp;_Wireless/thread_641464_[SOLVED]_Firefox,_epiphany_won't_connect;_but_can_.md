---
title: "[SOLVED] Firefox, epiphany won't connect; but can ping www names (not ipv6 issue)"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by haecceity on 2007-12-15
Hello,

Running Ubuntu 7.10

I can ping names like [www.google.com](www.google.com) and get a resolve + response.

Browsing by name works in Konqueror (and Lynx!) but not in Firefox or Epiphany.  It *used* to work in Firefox but I've had to spend hours playing with the wireless connection (dreaded Broadcom 4306) and the end result is this.

All the posts I've found on this boil down to "disable ipv6", which I've done both in "about:config" and in /etc/modprobe.d/aliases

Have tried rebooting and everything else I can think of.  This is driving me nuts...Konqueror feels like a blunt tool for browsing the web after using Firefox.

---

### Post by haecceity on 2007-12-16
Does anyone at least have an idea how I can troubleshoot this?

It seems telling to me that Konqueror & Lynx work fine, but not Firefox.  I'm pretty sure it's something I did while trying to get the flakey wireless to behave.

---

### Post by haecceity on 2007-12-19
Found the problem.  I'll explain in case it happens to anyone else.

My 'hosts' file was messed up.  I do use a custom hosts file to block adware etc. but I haven't touched it for months, so I don't know how it got corrupted.  Also not sure why only Firefox and Epiphany were affected by this.

---

