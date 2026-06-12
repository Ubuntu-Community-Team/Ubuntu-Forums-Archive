---
title: "[SOLVED] NFS will result in 99.9% Waiting time on client"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Archmage on 2007-12-04
When I try to accecs a nfs-share, my client has 99.9% waiting time. The whole system is slow. (E.g. opening an empty tab in firefox will take 30 minutes.)

Anyone have a clue what is causing this problem?

---

### Post by Friek on 2007-12-06
That depends on the link between your box and the NFS server ;)
If it's waiting, the NFS mount is basically just dead.

Try mounting your NFS mount with -o tcp to check if that improves anything.

---

### Post by Archmage on 2008-01-16
It was the fault of the router. (Only 0,1% of all network was working.)

---

