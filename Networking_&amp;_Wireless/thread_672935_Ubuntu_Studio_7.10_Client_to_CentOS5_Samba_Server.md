---
title: "Ubuntu Studio 7.10 Client to CentOS5 Samba Server"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by Frankly3D on 2008-01-20
CentOS5 samba Server with both Linux and MS clients.

The problem client Ubuntu Studio 7.10 created using : 
[http://tinyurl.com/24rjvx](http://tinyurl.com/24rjvx) (Ubuntu Forums)

smbclient --list shows all server shares.

fstab has
//Server/ShareX   /home/User/Share            cifs  credentials=/etc/auto.smb.USER 0 0

hosts Ubuntu has: 192.168.0.12 Ubuntu
/etc/samba/lmhosts has 192.16.8.0.X Server

/etc/auto.smb.USER chmod 600 as root 

dmesg | tail is giving me cifs mount error 22, and no username specified.
Which I figured credentials has taken care of.


Any thoughts
Frank

---

