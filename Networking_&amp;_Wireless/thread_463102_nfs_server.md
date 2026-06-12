---
title: "nfs server"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by tj71587 on 2007-06-03
Hey there, I'm making an nfs server and following the steps on ubuntguide.org, and I was just wondering how I make a windows system see it and assign it to a letter (ie the T: drive).  Also, I am trying to even access it by giving the manual mounting command and it tells me mount:192.168.1.5: etc/export failed, reason given by server: Permission denied. (btw i did create a new folder named export inside etc just for this)

Thanks,

T.J.

---

### Post by kidders on 2007-06-04
Hi there,

Windows is pretty much the only OS with no native support for NFS. You might be able to find an NFS client for Windows ... I have no idea if one exists. Alternatively, you could use the Windows filesharing protocols to share your files.

> **tj71587 said:**
> Also, I am trying to even access it by giving the manual mounting command and it tells me mount:192.168.1.5: etc/export failed, reason given by server: Permission denied.

You should check your NFS server's /etc/export_**s**_, to make sure you're authorised to access the share. Also, make sure you're addressing it correctly. Incidentally, sharing directories in /etc is probably not a good idea.

[SIZE="1"][COLOR="Silver"][UAResolved][/COLOR][/SIZE]

---

### Post by cornsnap on 2007-06-04
You can download the nfs client for windows at microsoft's site.

---

### Post by EmmEff on 2007-06-04
Stick with Samba...  MS' NFS client is pretty bad.

---

