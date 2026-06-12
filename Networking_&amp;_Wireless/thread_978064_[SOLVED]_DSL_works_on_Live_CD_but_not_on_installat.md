---
title: "[SOLVED] DSL works on Live CD but not on installation!"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2008-11-10
Hi,
I installed 8.10 Desktop on a computer at work. When I first ran a live CD session, Ubuntu successfully accessed my DSL connection automatically on interface eth0. After actually installing the OS, however, even pppoeconf fails.
Not only is there no real eth0 interface (just something called ifupdown(eth0)) but there's no MAC address either. Also, when I go into Network Manager (even using sudo) on the installed Ubuntu, I'm not allowed to add a new interface or edit the existing one ("no new connecdtions allowed").
What's wrong with my installed settings?
Any ideas?
David

---

### Post by dbclinton on 2008-11-11
Just for the benefit of others, I discovered other posts to this forum that directly related to this problem. One should edit /etc/network/interfaces and remove everything except 

[INDENT]auto eth0[/INDENT]

This seemed to work for others and it certainly did the job for me!

---

### Post by dbclinton on 2008-11-13
I realized that this whole problem was probably my fault:
The first thing I did after installing 8.10 was run pppoeconf to setup my DSL access. I now realize that my DSL provider (Acanac) had pre-configured the modem to require no logon at all and my pppoe activity served only to mess up Ubuntu's network settings! Eliminating all the extra lines in interfaces simply fixed the mess I'd made.
Hope this helps others...

---

