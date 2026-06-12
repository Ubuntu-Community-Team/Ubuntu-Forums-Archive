---
title: "How to share NFS drive content to web port 80 using apache ?"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by albertwt on 2010-11-02
Hi All,

My goal is to provide file access through HTTP to all of my NFS shared drive that i dedicated for public access.

Is it possible to create a website using HTTP which list all of the contains of my NFS shared drive to the public ?

it is failed even just to showmount, in Windows i usually access it using \\10.2.2.50\Volume_1 on the windows explorer.

FYI: this is D-Link DNS-323 NAS device.

```
root@sv6:/etc/apache2# apt-get install nfs-common

root@sv6:/etc/apache2# showmount
clnt_create: RPC: Program not registered

root@sv6:/etc/apache2# showmount -e 10.2.2.50
clnt_create: RPC: Port mapper failure - RPC: Unable to receive
```

Thanks.

---

### Post by Ocxic on 2010-11-02
yes, just set your NFS drive/folder as your root web folder in Apache.

if you access it in windows like you say with \\10.2.2.50\Volume_1
go to you places menu, and select connect to server.

choose Windows Share from the drop down menu.
put 10.2.2.50 in the server field
and "Volume_1" in the share field, and click connect

---

### Post by bioterror on 2010-11-03
> **Ocxic said:**
> yes, just set your NFS drive/folder as your root web folder in Apache.

I would do this with a symlink (ln -s).
For a mystical reason I'm not just seeing the idea of putting Apaches root to NFS share.

---

### Post by Ocxic on 2010-11-04
you could actually do either. it's up to you. a Simlink might be more manageable tho.

---

### Post by albertwt on 2010-11-04
> **Ocxic said:**
> you could actually do either. it's up to you. a Simlink might be more manageable tho.

great, so i should symbolic link the apache root dir into the NFS share ?

or shall I edit apache2 **httpd.conf** file ?

cmiiw.

---

### Post by Ocxic on 2010-11-05
a link would be easier to manage. i would go with a link.

---

