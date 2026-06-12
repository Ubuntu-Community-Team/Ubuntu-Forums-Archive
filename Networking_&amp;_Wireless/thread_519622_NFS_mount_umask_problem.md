---
title: "NFS mount umask problem"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by sitedesign on 2007-08-07
I have a small network with Ubuntu workstations and an Ubuntu server.

I have NFS server set-up to share files on the server.
I have the workstations mounting the NFS share in the fstab which works fine.

The problem is that when a user creates a file or folder on the share from the workstation it is created with user only writes.

How can I change it so that other users in the same group can read and write the files on the shares. I presume I need to change the umask somewere, but where? On the server or on the clients?

I would need it to be that users create all files and folders as read and write for members of their group ID on the server. I have got around the matching groupid's on the clients and server but that is a pain as well.

I am only doing this to get around some issues with samba and openoffice on linux clients.

Any help much appreciated.

---

### Post by mdr on 2008-03-18
Same problem here.

any answers ?

---

### Post by Eiríkr on 2008-03-19
Your easiest bet is actually to use filesystem permissions on the folder(s) containing the items you want shared among group members, by making judicious use of the [font=courier]chmod[/font] command, particularly with regard to the [font=courier]setgid[/font] bit.  Have a look at [post=4423357]this post[/post] for some instructions on how to set this up; the post is mostly about Samba setup, but there's a section in there about filesystem permissions that should cover exactly what you're talking about.  

Cheers,

Eiríkr

---

### Post by mdr on 2008-04-21
tried setgid to no avail.

however by changing the default umask in /etc/profile to 0007 on each client I was able to get default group read and write.

---

