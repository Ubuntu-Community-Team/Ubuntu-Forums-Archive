---
title: "[SOLVED] kernel 2.6.24-19-generic and Port 4000"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by Capheind on 2008-07-16
SOrry for the duplicate posting but the title of the last was incorrect and I've figured out a few more things. Yesterday I ran some automatic updates which updated the kernel to version 2.6.24-19-generic, and now when I do an Nmap against my IP I see port 4000 open, but it doesn't do this if I boot into kernel 2.6.24-16-generic. Is this a bug, some new feature? What gives

---

### Post by Capheind on 2008-07-20
A reinstall solved it, but after the fact I found the article below which probably would have helped in figuring out what exactly was running on that port.

[http://www.hackinglinuxexposed.com/articles/20030515.html](http://www.hackinglinuxexposed.com/articles/20030515.html)

---

