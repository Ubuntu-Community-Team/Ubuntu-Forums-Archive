---
title: "How to flush DNS cache?"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by Aleksandersen on 2006-12-27
Hi,

How can I flush the DNS cache on Ubuntu systems?

---

### Post by ronmonki on 2007-02-28
I would like the answer to this too.

anyone know?

---

### Post by fstab on 2007-03-19
I don't think Ubuntu uses any DNS cache by default.  I tested this by running a "host" command, then disabling my network device and running the same "host" command.  It didn't return anything, so it appears that my workstation is not caching DNS info.

There is a package called nscd that caches dns names and our DNS server uses it, but I don't think it's something a workstation would need.  To clear the cached DNS names on our server, I run /etc/init.d/nscd restart.

---

### Post by gardara on 2007-03-23
> **fstab said:**
> I don't think Ubuntu uses any DNS cache by default.  I tested this by running a "host" command, then disabling my network device and running the same "host" command.  It didn't return anything, so it appears that my workstation is not caching DNS info.

There is a package called nscd that caches dns names and our DNS server uses it, but I don't think it's something a workstation would need.  To clear the cached DNS names on our server, I run /etc/init.d/ncsd restart.

/etc/init.d/ncsd: No such file or directory

and as root:

/etc/init.d/ncsd: command not found

---

### Post by fstab on 2007-05-02
/etc/init.d/ncsd: No such file or directory

- That should have been "nscd", I edited the previous post.  Make sure to install the nscd package beforehand too.

---

