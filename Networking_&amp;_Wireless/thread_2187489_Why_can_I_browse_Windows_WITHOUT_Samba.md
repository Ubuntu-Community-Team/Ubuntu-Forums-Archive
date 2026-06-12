---
title: "Why can I browse Windows WITHOUT Samba ?"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by charlieprime on 2013-11-12
Somehow I am able to browse Windows 7 computers on my home network using Thunar WITHOUT Samba installed.

I cannot figure out why! :o

Anyone have ideas?  Perhaps I installed some Thunar or Midnight Commander plug-in which caused this?

---

### Post by Morbius1 on 2013-11-12
Samba the server package is not installed by default but that is a package that creates a samba server on your Linux box so that others can access your shares. 

Smbclient the samba client is installed by default and that is the package that accesses SMB ( Windows ) and Samba shares that reside on someone else's machine.

---

### Post by charlieprime on 2013-11-12
I think that's it!

```
charlie@acerbox:~$ dpkg -s smbclient
Package: smbclient
Status: install ok installed
Suggests: cifs-utils

charlie@acerbox:~$ dpkg -s cifs-utils
dpkg-query: package 'cifs-utils' is not installed and no information is available
```

I've grown weary of fighting with Samba.  smbclient seems to accomplish what I want.  I'm going to make sure all my machines have it.

Thanks man!

---

### Post by dannyboy79 on 2013-11-12
as long as you don't intend to share files "FROM" ubuntu, smbclient should be fine for browsing SMB network shares.

---

