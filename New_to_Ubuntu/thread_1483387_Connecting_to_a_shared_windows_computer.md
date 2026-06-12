---
title: "Connecting to a shared windows computer"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by patentrich on 2010-05-14
So, I'm sure you get this one alot, but I've been knee deep in Samba all afternoon, and cannot get my newly installed ubuntu 10.04 to connect to my office's windows network.

Here's the info I have.

The workgroup name is: DOMAIN
The domain name is blank
The partition I wish to connect to on the windows network is MACH-14\E
The network has a password.
The username I wish to use is MACH-22 (and is registered on the server already)

Help, please.

---

### Post by -humanaut- on 2010-05-14
Easiest way I've done it is like this:

Go to Network Folder under places type smb://windows.ip.address
then hit enter make SURE that windows is setup on the ether end to receive the connection.

---

### Post by patentrich on 2010-05-14
how do I get it to give me a box to type into?

---

### Post by spiky001 on 2010-05-14
Ctrl+l

---

### Post by patentrich on 2010-05-14
Thanks, it worked.  Now, to install FilePro

---

### Post by -humanaut- on 2010-05-14
Please mark this thread as Solved thanks.

---

### Post by patentrich on 2010-05-14
How do I mark it as solved?

---

### Post by new_tolinux on 2010-05-14
Click "[Thread  Tools]("http://ubuntuforums.org/showthread.php?t=1483387&nojs=1#goto_threadtools")" at the top right of this topic.

Edit: not the link in this message, you have to use the link at the top of this page.

---

