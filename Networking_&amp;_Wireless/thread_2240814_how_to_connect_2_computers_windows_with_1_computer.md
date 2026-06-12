---
title: "how to connect 2 computers windows with 1 computer ubuntu studio 14.04"
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by hbbco on 2014-08-22
[SIZE=1]I recently installed ubuntu studio 14.04 and I want to set up a small home network with two computers, one with windows 8 and the other with windows 7 The network between windows computers works perfectly, but Windows Explorer does not show my computer ubuntu. The same is true when I use Ubuntu [/SIZE][SIZE=1]Nautilus.

To the above I installed ubuntu SAMBA 4.1.0. The strange thing is that when I set up the network, it worked, even after reboot all computers, but now does not work between two computers Ubuntu and Windows. The following is the smb.conf file:


I have not put passwords in Samba, do not interest me. The smbtree sudo command provides the following response:
[/SIZE]
```
hugo@hugo-P35-DS3L:~/Archivos_correo$ sudo smbtree
[sudo] password for hugo: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Enter root's password:
```

Can you help me?

---

### Post by TheFu on 2014-08-22
Please post the output for both
```
testparm
smbtree
```
in code tags. No need for "sudo".

---

