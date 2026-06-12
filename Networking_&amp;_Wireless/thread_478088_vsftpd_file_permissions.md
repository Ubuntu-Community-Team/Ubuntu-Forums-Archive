---
title: "vsftpd file permissions"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Garf on 2007-06-19
Hi...

I upload files through dreamweaver onto my Ubuntu 6.06 server via vsftp...

Basically the problem is that once a new file has been uploaded, the permissions are -rwx------ Meaning that if I want to view the file I just uploaded on the web, I have to change permissions manually..

I can't see in vsftp anywhere to change that. I am not uploading to /var/www/ it's in ~/htdocs/

Is it a security thing for vsftp whereby you can not do this at all, or am I missing a setting?

I realise that it is *Very Secure* to have those permissions, but it's not what I want for now...

Thanks in advance.

---

### Post by Mr. C. on 2007-06-19
What type of user are you connecting as: anonymous, real, virtual ?

The setting that controls file/directory creation for anonymous users is **anon_umask**, 
and for local users it is **local_umask**.  Set the appropriate one to a more permissive value (like 002, or 000).

MrC

---

### Post by Garf on 2007-06-19
connecting as a user thats already on the system

---

### Post by Mr. C. on 2007-06-19
Ok, so did you set local_umask in your /etc/vsftpd.conf file  and restart vsftpd ?

MrC

---

### Post by Garf on 2007-06-20
Yeah thanks... that works.

---

