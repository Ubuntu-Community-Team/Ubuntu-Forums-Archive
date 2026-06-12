---
title: "Completely Stumped - Workgroup Problem"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by Fletch273 on 2008-07-12
I've been trying to set up my home network for two days now.  I've searched everywhere but can't find a definite answer.

The problem is that I'm running Ubuntu on an old PC of mine, and my other laptop is WinXP.  I've finally managed to see the XP laptop in Ubuntu, but I can't see Ubuntu in my workgroup on the XP computer.

I am able to ping each computer from either side.  I can even transfer files across into XP using the 'run' function in Windows (run - \\<ip address>).  My problem is that I would like them all to appear in the same workgroup but my network is having none of it.

Does anyone know what I could be doing wrong?  I have samba and everything thanks to searches in other threads.

---

### Post by superprash2003 on 2008-07-12
go to the terminal and type sudo gedit /etc/samba/smb.conf . there you would find an option to change Workgroup name from WORKGROUP to whatever you wish..replace WORKGROUP with whatever you want.. then save and close the file.back in the terminal type sudo /etc/init.d/samba restart ..

---

### Post by Fletch273 on 2008-07-12
Yeah, I've found that in the other threads.  Thanks anyway though.

---

