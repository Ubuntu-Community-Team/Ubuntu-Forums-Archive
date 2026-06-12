---
title: "mac OS X connecting to ubuntu server"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by bugboy on 2006-10-28
I've got a ubuntu lamp server running and NFS working

I can connect to the server fine with fugu but was wondering how can i mount the ubuntu server on my mac like i do with other mac computers.

If i go via connect to server and type 

nfs://192.168.0.8:ubuntu

i get password and user name wrong where do i put these as i'm never asked for them.

I tried working netatalk working but it seemd not to want to work

any help would be great

---

### Post by bugboy on 2006-10-28
i have now got samba working

i've heard though that this can sometimes mess with the file forks.

Has anyone got a walf through for NFS which works.

Cheers

---

### Post by mike3k on 2006-10-28
To use NFS with Mac OS X, you need to specify insecure in your exports. You can then mount it as nfs://192.168.0.8/home

---

### Post by handy on 2006-10-28
> **bugboy said:**
> i have now got samba working

i've heard though that this can sometimes mess with the file forks.

Has anyone got a walf through for NFS which works.

Cheers

I don't know if you still need this?

[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT)

---

