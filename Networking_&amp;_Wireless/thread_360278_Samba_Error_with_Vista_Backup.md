---
title: "Samba Error with Vista Backup"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by ercdvs on 2007-02-13
I have samba set up and running just fine on 6.10, with a very simple smb.conf:

> workgroup = WORKGROUP
netbios name = Ubuntu
encrypt passwords = yes

[homes]
read only = no
browsable = no

[music]
path = /home/tvbox/music
browsable = yes
write list = tvbox
public = yes

[video]
path = /home/tvbox/video
browsable = yes
write list = tvbox
public = yes



I can map, connect, browse, read & write to these shares as my 'tvbox' user with no trouble via a normal interface.

However, when I attempt to point the Vista backup program to the samba share, I see the following error in the samba log :

> 
[2007/02/12 23:08:57, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/02/12 23:08:59, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!

I was pointing to /home/tvbox/backup.. and if i browse that directory, i can see directories created with the tvbox user and proper permissions.

Using the latest samba from apt-get ...

Any thoughts on what to try ?

---

