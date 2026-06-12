---
title: "What's the best way to set up a linux-linux-windows network?"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by sab0403 on 2007-06-22
Ok, here's the deal. I have two PCs running Ubuntu 7.04, and one (possibly two) running Windows Millenium. What's the best way to set them up?

I thought NFS, but I don't know if Windows supports that. Do I need Samba? Do I *have* to use a server/client architecture, or is there a way to make no particular PC the server?

Thanks in advance.

---

### Post by steve0921 on 2007-06-22
I don't think that windows supports NFS, so you'll have to use samba.

Neither samba or nfs though are client/server systems in the way you're thinking. Any computer on which files are accessed must run a server ("samba" server is built in to windows) and any computer that accesses files on another must do so with a client. Thus in an all-sharing network, every computer will be both a client and server.

---

