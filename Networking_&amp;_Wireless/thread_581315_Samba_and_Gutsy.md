---
title: "Samba and Gutsy"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by fettuohi on 2007-10-19
I'm trying to get samba to run under gutsy but for some reason smbd won't start. I'm using my smb.conf file from feisty and every time I

gd1331@ANDRE:~$ sudo /etc/init.d/samba restart
Stopping Samba daemons...:.
Starting Samba daemons: nmbd.
gd1331@ANDRE:~$ sudo /etc/init.d/samba start
Starting Samba daemons: nmbd.
gd1331@ANDRE:~$

only nmbd is started or restarted but not smbd. Any ideas?

Kind Regards

André

---

### Post by fettuohi on 2007-10-19
Well, I finally got samba running. So my windows machines can see my samba server but I can only connect through entering the ip address of the server on my windows machines. If I click on the computer name of my samba server I get an error saying can't resolve the computer name. I know I'm missing something in my smb.conf but I can't figure out what.

Regards

André

---

