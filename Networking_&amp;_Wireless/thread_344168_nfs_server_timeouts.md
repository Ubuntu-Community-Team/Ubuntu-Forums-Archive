---
title: "nfs server timeouts"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by zeldor on 2007-01-22
so I have a ubuntu machine (desktop install) that has a filesystem exported via NFS.
other machines, in this case a fedora 3 machine, mount that directory via autofs/nis.
the problem I have is that the mount times out really darn fast on the other machines.
If Im running a job that doesnt touch the filesystem for a bit and then goes to
write a file it cant find the filesystem as it was unmounted. My desktop was fedora before
and I never had this problem so its something with the way things are setup on ubuntu.
anyone have any thoughts?  I had thought I might need the server install of ubuntu
but didnt know if that was any different then desktop with the kernel level nfs server
installed.

thanks.

---

