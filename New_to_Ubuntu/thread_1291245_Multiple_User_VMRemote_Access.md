---
title: "Multiple User VM/Remote Access"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by jimsheep on 2009-10-14
hi all;

due to some over-zealous firewall activity :twisted: i am no longer able to access certain things.  i'd like to get around this  by enabling remote access across the internet.

i'm running ubuntu 8.10 behind a router on a broadband connection (10 Mbps).  i'd like to set it up so that i can share a guest session for a co-worker and still access my own account.  does this mean i have to run both in separate virtual machines?  is this even possible?

i looked at **[this]("http://ubuntuforums.org/showthread.php?t=953163&highlight=Multiple+User+VM%2FRemote+Access")** post, but it didn't seem to help.  i am not able to install the windows vnc viewer; the clients all have the remote desktop connection app that comes with XP.

input and probing questions are most welcome.

---

### Post by Sarmacid on 2009-10-14
You can have plenty of accounts and users connected at the same time on linux if you use the cli, however for GUI I really don't know how to acomplish that. Maybe tunneling the remote desktop viewer through ssh so you can access your desktop and then tunnel through ssh for your coworker and launching an additional display.

---

### Post by jimsheep on 2009-10-14
is there a how-to for that? i'm not familiar with IP tunneling or anything like that.  i'm familiar with following instructions, and am familiar with CLI usage.  i just don't know the specifics.

---

### Post by jimsheep on 2009-10-14
bump.

---

### Post by jimsheep on 2009-10-15
bump.

---

