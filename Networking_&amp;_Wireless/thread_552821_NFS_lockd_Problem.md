---
title: "NFS lockd Problem"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by foxylad on 2007-09-17
I have three dapper machines, one configured as a server and two clients. I did an update on one client this morning, which included upgrading the kernel to 2.6.17-12 generic, and now NFS is not working.

The other client is still working, so I am assuming the server is OK. The bad client times out - when I try a manual mount, I get "mount: RPC: Timed out". The server shows "Sep 17 07:56:29 ruru2 mountd[4165]: authenticated mount request from 10.50.18.74:843 for /var/shared (/var/shared)".

The oddest thing is when I do "rpcinfo -p" on the client, it shows:

    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    1024  status
    100024    1   tcp    3027  status

Note there are no nlockmgr entries, as there are on my other client. All my config files haven't changed, so I won't add them to this post, but if anyone thinks they will help, let me know. Any ideas?

Thanks!

---

### Post by foxylad on 2007-09-17
UPDATE...

The problem is to do with DNS. When I add the client to the server hosts file, it works. This doesn't explain why it has worked up to now, nor why the other client works, so back to Google...

---

