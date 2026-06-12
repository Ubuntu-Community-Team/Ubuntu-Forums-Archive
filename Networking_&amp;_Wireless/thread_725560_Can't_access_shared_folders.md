---
title: "Can't access shared folders"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by jasad on 2008-03-15
Hi.  I'm a relative newbie with Linux and I'm trying to transfer files from an old laptop running Ubuntu 7.10 to a new laptop running the same.  I've enabled sharing on the folders I want to move, and I can see both machines in my network places, but there are no folders when I access them.

Any advice?

Thanks

---

### Post by Iowan on 2008-03-15
How are you attempting to share them - NFS, Samba, FTP, SSH?  Most require an additional package to be installed on the source (server) machine.

---

### Post by jasad on 2008-03-15
I installed NFS and SAMBA.  I get the same results trying to share with either method.

---

### Post by superprash2003 on 2008-03-16
try this smb://192.168.1.10 where 192.168.1.10 is the ip address of the pc you want to connect to

---

### Post by jasad on 2008-03-16
thanks for the reply.  I've been monkeying with this for a couple of days now and I'm making no headway.

I tried smb://192.168.0.3 (machine i'm connecting to) and got the message

No such file or directory.

I've determined that at least part of my problem is firewall configuration as I can't see the computer on the network at all unless I stop firestarter.

Nonetheless, even when firestarter is down and I can see the computer in my workgroup, I still can't access the shared folder.  I get the message:

The folder contents could not be displayed.

I have permissions on the shared folder set as wide open as they can be for everybody, so I don't think it's that either.

I really need to swap my data between these 2 machines asap, so If anyone has any suggestions, I would be most appreciative.  :)

J

---

### Post by superprash2003 on 2008-03-16
you probably might have some problems with your samba setup.. try following this guide and set it up again [http://ubuntuguide.org](http://ubuntuguide.org)  .. if this doesnt help please insert the smb.conf file here

---

### Post by fsmithred on 2008-03-17
NFS and Samba require some configuring to get them working. SSH/SFTP is easier.

On one machine:

sudo apt-get install ssh


On the other machine, open your file browser, Go --> Location
Then put in the address bar (assuming you use the same login name on both machines)

sftp://192.168.0.3

Log in, select, copy and paste files.

---

### Post by Eiríkr on 2008-03-17
Ditto for fsmithred -- Samba and NFS can be quite complicated to set up (Samba much more so), and while they're great when needed, they can be a bit much.  Meanwhile, SFTP is quick and simple for sharing between two Ubuntu machines.  

Cheers,

Eiríkr

---

### Post by jasad on 2008-03-17
Thanks for the responses all.  I managed to get an NFS share working following this guide:

[http://doc.gwos.org/doku.php/doc:network:nfs?s=samba](http://doc.gwos.org/doku.php/doc:network:nfs?s=samba)

I didn't think it was working at first because I kept getting errors when I tried to mount the share, but it turns out that it mounted just fine.

Next time I'll know to try sftp.

---

