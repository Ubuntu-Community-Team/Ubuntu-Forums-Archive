---
title: "Map to home directory from XP"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by iancvt55 on 2008-02-18
Hi

My Ubuntu PC can see and read files on the XP machine using Samba.

How do I map from the XP machine to my home directory on the Ubuntu PC?

Thanks

Ian

---

### Post by Existentialist on 2008-02-19
From the shared folders application you can set your home directory to be shared and then on the xp machine go to my computer, tools > map network drive.  Enter:
\\192.168.x.xxx\sharename
Where the ip is the ip address of the linux box, and sharename is whatever you set the share up to be in Ubuntu.

---

