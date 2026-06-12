---
title: "Do I need samba to share file between Ubuntu and XP?"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2008-08-11
Do i have to install ubuntu to share files between windows and ubuntu? I want the windows shares to be visible on ubuntu and the ubuntu shares to be bisible on ubuntu.

---

### Post by c2olen on 2008-08-11
Uhm, yes, but that's just because Windows does not support NFS without the use of some commercial third party tool for NFS support.
So, if you want to share files between a Unix and Windows machine, you need to use SAMBA on the Unix box, of NFS clients on the Windows box. When using NFS however, you still need to set up the NFS server on the Unix box. NFS servers are very easy to configure though, compare to SAMBA.

Fortunately, there's tons of good howto's on setting up SAMBA and NFS, so feel free to google around...

---

### Post by Iowan on 2008-08-11
[Here]("https://help.ubuntu.com/community/SettingUpSamba") is a good starting place for Samba.  [SSHFS]("https://help.ubuntu.com/community/SSHFS")  is another option - though I don't know how easy it is on Windows.

---

### Post by TDragon on 2008-08-11
There's a nice utility that sets up Samba for you in the Add/Remove Programs section. Just type Samba in the search box and you should be able to find it easily. I'll try to post the name of it when I get back home.

---

