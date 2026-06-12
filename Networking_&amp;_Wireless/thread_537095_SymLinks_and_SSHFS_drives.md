---
title: "SymLinks and SSHFS drives"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by TheFuzzy0ne on 2007-08-28
Hi. I have a server on my local network, and for almost every user on the server, there is a corresponding PC. Basically, each user has their home directory on the server mounted on their own machine. I have some stuff I'd like to share, so I have set the permissions for the directory, to allow other users to view it. The problem is, the symlinks all work on the server, but when a user opens up the network share, and they try to follow the symlink, it looks on their local machine instead of on the server in the directory inside my home directory which I conveniently named "share".

I would appreciate any input you may have to offer on the best way to achieve what I am trying to do. Should I just create another user account (like "share" or "anonymous", and let all users login to that? It doesn't sound very secure, but this is only a local network, so it shouldn't be a problem.

Many thanks in advance.

Daz.

---

### Post by TheFuzzy0ne on 2007-09-15
*boing boing*

---

### Post by kevmitch on 2008-02-06
I'm not sure I fully understand how sshfs fits into your "network share" scheme, but I gather that the bottom line is that you want the symlinks on the system you're sshfs'ing to to be followed to the directories they point to on that machine. I have managed to achieve this by putting a line for the sshfs mount in my /etc/fstab that looks like

sshfs#server.domain.com: /media/mountpoint fuse defaults,users,noauto,follow_symlinks 0 0

Note the "follow_symlinks" option. You can do the equivalent on the fly on the command line by typing 

$ sshfs -o follow_symlinks server.domain.com: ~/mnt

---

### Post by TheFuzzy0ne on 2008-02-09
Wonderful! Thanks. :)

---

