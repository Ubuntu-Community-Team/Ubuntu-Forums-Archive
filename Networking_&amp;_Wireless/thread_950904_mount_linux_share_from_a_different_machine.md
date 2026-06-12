---
title: "mount linux share from a different machine"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by tone33 on 2008-10-17
I have one machine that is my media server (debian) with a linux file system as part of my LAN.  I want to mount that media server drive/share on my other ubuntu machines.  Is there a how-to guide out there?

---

### Post by ww711 on 2008-10-17
NFS is probably what you are after.

Have a look at this article.

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by tone33 on 2008-10-17
that's exactly what i needed - works great!  thanks!

---

### Post by tone33 on 2008-10-18
is there any way to allow write access to the exported share to a non-root user?  I want to be able to mount it to any client machine on my LAN and allow the client to rip a cd to the music share.

---

### Post by superprash2003 on 2008-10-19
yes, by using rw instead of ro in your /etc/exports

---

