---
title: "Portmap and hosts.deny"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by Zill on 2008-01-03
I run NFS and have portmap installed on both the server and client.  In the client hosts.deny file I have the line "ALL: ALL".  I have also tried adding the lines "portmap: ALL" and "portmap: ALL : deny".  However, even with no entries in the hosts.allow file, the remote directory is still mounted correctly by NFS/portmap.

Please clarify which is the correct syntax for the hosts.deny file:
1  ALL: ALL
2  portmap: ALL
3  portmap: ALL : deny

Does "ALL" implicitly include portmap?

Any suggestions as to why my hosts.deny file appears to be ignored?

---

