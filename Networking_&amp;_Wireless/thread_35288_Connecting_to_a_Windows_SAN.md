---
title: "Connecting to a Windows SAN"
date: 2005-05-18
forum: Networking &amp; Wireless
---

### Post by JaF on 2005-05-18
Hi guys,

I can browse to the windows SAN on my office network using places=>Network Servers but I can't mount it. Does anyone know how I can set it up so that it mounts on startup?

---

### Post by alastair on 2005-05-18
A "share" I assume, not a "SAN".

See :

man smbmount

and look to edit the /etc/fstab file.

---

### Post by JaF on 2005-05-19
I've tried looking at the man pages but it hasn't really got me very far. It doesn't seem to mention anywhere about the domain???

---

