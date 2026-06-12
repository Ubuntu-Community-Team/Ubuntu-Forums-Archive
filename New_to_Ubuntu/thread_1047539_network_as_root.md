---
title: "network as root"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-22
how does one access the network shares as root, "gksu nautilus" don't work.

---

### Post by SamNSane on 2009-01-22
What are you trying to do? Exactly.

Launching anything with elevated privs locally doesn't give you any extra privs out on a network. The systems out there all have their own permissions setups, unless your system is a member of a domain and you are operating as a domain admin.

---

### Post by bodhi.zazen on 2009-01-22
We need more information as it depends on the network protocol ie samba, NFS, ftp, etc ...

With some of these protocols it may not be possible.

---

