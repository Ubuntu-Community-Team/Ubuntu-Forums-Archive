---
title: "Trying to create network share"
date: 2021-02-24
forum: Networking &amp; Wireless
---

### Post by jessica43928 on 2021-02-24
I would like to build an ubuntu network share that my (windows) work laptop can see, probably some type of RAID system.  I currently have several ubuntu machines, including some shared folders that other ubuntu computers can see, but the windows laptop doesn't see anything on my home LAN except (for some reason that I don't understand) it does see my MythTV machine (running ubuntu).  I don't have access to change much of anything on the windows computer, but if MythTV can do it, obviously I should be able to do it somehow, right?  Does anyone have any ideas of what would work?

---

### Post by TheFu on 2021-02-24
[https://ubuntu.com/server/docs/samba-introduction](https://ubuntu.com/server/docs/samba-introduction)
and
[https://ubuntu.com/server/docs/samba-file-server](https://ubuntu.com/server/docs/samba-file-server)

For Unix-to-Unix, NFS is generally best., but that has some added mandates.  The server guide has instructions if that interests you.

Both samba and nfs can be used.

---

