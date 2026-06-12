---
title: "AFS Client filesystem size limitation of 8.6GiB"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by pjomega on 2008-06-14
I suppose this qualifies as "networking" so here goes...

The openafs client creates an afs mount at /afs and tells the system that the filesystem has 9GB/8.6GiB of space available to it:

% df -h /afs
Filesystem            Size  Used Avail Use% Mounted on
AFS                   8.6G     0  8.6G   0% /afs


The actual space available of course depends on the afs volume quotas, which the asf client may or may not be able to read, depending on the cell ACLs, so the client generates a fake value. My volume quota/server disk space available exceeds this 8.6GiB limit. This presents a problem when trying to copy a file or a group of files whose size exceeds this, since neither cp nor nautilus are particularly keen on letting you copy more data than they think the mount can hold. 

Does anyone know how to either 1) increase the apparent free space of the /afs mount or 2) copy files ignoring the available free space limitation?

Many thanks.

---

