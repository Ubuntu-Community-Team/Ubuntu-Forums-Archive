---
title: "[SOLVED] How do I share folders in samba?"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2008-05-30
Hi, all.

Despite reading through several threads on similar subjects, I can't seem to find instructions on how to do something which seems like it should be quite simple:

How do I share folders/files on my ubuntu machine via samba with my vista pc?

I've already got the two pcs connected.  My vista box sees the ubuntu box, but when I try to browse the network it doesn't see anything but ubuntu's printer/pdf info.

I need to share at least my home folder, and if possible I'd like to share a second hard disk (/media/disk).

Please note that I have ubuntu studio 8.04.  It should work the same as plain-jane ubuntu, but maybe not...

Any help would be much appreciated!

---

### Post by hurtstotalktoyou on 2008-05-30
ttt

---

### Post by superprash2003 on 2008-05-30
right click on the folder you want to share and click on share folder and click on SHARE.. if you still have problems paste your smb.conf file here.. in the terminal type sudo gedit /etc/samba/smb.conf and paste the contents of smb.conf file .. you may also want to read a samba guide [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by hurtstotalktoyou on 2008-05-30
> **superprash2003 said:**
> right click on the folder you want to share and click on share folder and click on SHARE.. if you still have problems paste your smb.conf file here.. in the terminal type sudo gedit /etc/samba/smb.conf and paste the contents of smb.conf file .. you may also want to read a samba guide [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

Muchos gracias!

---

