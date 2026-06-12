---
title: "NFS Version"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by AmericanAqualung on 2007-07-04
So I've been using NFS on my linux cluster for quite some time now under Dapper.  I'm trying to determine which version of the protocol is actually being used.  When I run 'rpcinfo -p' on both my head node (the nfs server) and on the other nodes (nfs clients), it tells me that version 2, 3, and 4 are running on the server and clients.  I installed using nfs-common and nfs-kernel-server.  The Ubuntu packages page doesn't help either.  Does anyone know which is actually being used?  Is it safe to assume that the latest version is being used?

Thanks,
Andy O'Hara

---

