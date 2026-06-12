---
title: "loging into a slackware box"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by zafoid on 2009-07-26
Hi, I have just installed Ubuntu desktop 9.04, I am running a slackware server with samba as the sharing protocol as I also have XP boxes on this network as well. Problem that I am having is that the ubuntu box is not logging onto the server file manager even though I have activated smbfs as a client. ANy suggestions???

---

### Post by superprash2003 on 2009-07-26
is the xp machine able to access the slcakware's samba shares?

---

### Post by swerdna on 2009-07-26
> **zafoid said:**
> Hi, I have just installed Ubuntu desktop 9.04, I am running a slackware server with samba as the sharing protocol as I also have XP boxes on this network as well. Problem that I am having is that the ubuntu box is not logging onto the server file manager even though I have activated smbfs as a client. ANy suggestions???

Does this mean that you can see the shares but not connect, or you can't even see them. Please explain more: "the ubuntu box is not logging onto the server file manager". It's a bit ambiguous.

---

### Post by Liolikas on 2009-07-26
In Linux world nfs (network file system) is more common. Samba is used only for Linux-windows connections. Set up nfs better.

[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

