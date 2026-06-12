---
title: "Different UID/GID on NFS server and client"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by prakash_prabhu on 2008-07-29
Hi

I am running a NFS server on Ubuntu 8.10 box while my client is on Ubuntu 7.04. On the server I am exporting some directories with UID and GID both being 1000. However, even though they are exported as read and write (rw in /etc/exports) I am not able to write to it since my client's mount directory UID and GID is 606 and 1003 respectively. Is there a way to specify (either in command line for mount or in the server's exports file) that the client user 606 should have rw access to the exported directories ?

thanks
Prakash

---

