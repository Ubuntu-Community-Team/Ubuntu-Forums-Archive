---
title: "Setting up an Ubuntu fileserver"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by DavidCain on 2008-08-03
Okay. So, I'm generally pretty technologically proficient, but sadly a complete idiot when it comes to anything related to networking. I'm getting a little better, but I digress. I need to set up a file server that several computers in my house can have access to (they'll all be Ubuntu machines- I already have a 100 GB Windows share the XP machines can use).

The server I have has two 160 GB HDs. I'm not asking for a tutorial on how to configure the server, but rather what the best way of setting it up is. Some people say SSH, some Samba and I'm just now finding other options like NFS and iFolder. I obviously want to utilize as much of that 320 GB as possible. What would work best? Thanks in advance.

---

### Post by rubenvazquez on 2008-12-17
well I can tell you how I set mine up.   I have a similiar situation.   I have an old hp with three HDD.  one 40 gb running the os (Ubuntu) and two 200 gb drives in raid 0.   Thats so I dont have to mount two seperate drives in my mac. I share my raid setup with samba.  As of right now I dont have any security setup.  I dont really think I need it, what do you all think?

My file server is headless and I connect to it using telnet.

Im not sure what the difference between samba, NFS iFolder is.

---

### Post by Iowan on 2008-12-17
My server has Samba - primarily "in case" the attached Windows machine needs to share.  I also installed SSHFS, but haven't really used it, yet.  NFS is supposed to be native to Unix.  This is the first I've heard of [iFolder]("http://www.ifolder.com/index.php/Main_Page").  Another option would be to install [NAS]("http://www.freenas.org/") software.

---

