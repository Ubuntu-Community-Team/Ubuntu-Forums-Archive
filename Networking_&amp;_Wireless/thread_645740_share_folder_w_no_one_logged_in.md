---
title: "share folder w/ no one logged in?"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by movrshakr on 2007-12-20
Is it possible to share a folder to the network without anyone being logged in? 

For example, turn on the computer, it ends up sitting at the login name screen...but at that point having a folder already shared.

---

### Post by Whiffle on 2007-12-20
Yep.  NFS shares or samba shares do this.  As long as Samba or NFS is running, the foler is shared.

---

### Post by movrshakr on 2007-12-20
> **Whiffle said:**
> Yep.  NFS shares or samba shares do this.  As long as Samba or NFS is running, the foler is shared.

But I have samba running, and it shares a folder in my /home/username area, but that folder is not available  to the net until I log in.

What do I change in smb.conf to make the share available before I log in?

---

