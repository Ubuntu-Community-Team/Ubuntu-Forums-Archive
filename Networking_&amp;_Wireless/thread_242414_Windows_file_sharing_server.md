---
title: "Windows file sharing server"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by djgrandmarquis on 2006-08-23
I'm trying to consolidate the four music collections in my apartment. So I'm trying to set up my three roommates' machines (running XP) as file sharing servers, and my Ubuntu Server machine as the client.

I've tried looking into FTP, SMB, and NFS, but I can't find any free servers for Windows. Essentially I'd just like to share a directory in Windows, preferably restricted by IP address.

Any suggestions?

---

### Post by djgrandmarquis on 2006-08-27
Problem solved: I've set up NFS servers via Cygwin.
[http://www.csparks.com/CygwinNFS/index.xhtml](http://www.csparks.com/CygwinNFS/index.xhtml)

Just make sure you mount the drives as noted in the tutorial. Works like a charm!

---

