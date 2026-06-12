---
title: "NFS lock up on concurrent use"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by isync on 2007-08-17
Hi all!

Sometimes on heavy concurrent use of NFS the shared directories and "everything nfs related" freezes on client machines while the server is working without error.

On client machines then, firing up the nautilus explorer fails, all that happens is that the rim of the window appears while the content renmains transparent

I found these entries in the logs:
kern.log:
Aug 17 10:49:16 localhost kernel: [632093.808649] rpc.nfsd[5294]: segfault at 0000000000000048 rip 0000000000409051 rsp 00007fffffce67d0 error 4

syslog:
Aug 17 14:36:03 localhost nfsd[27027]: fd cache inconsistency! 
Aug 17 14:36:10 localhost nfsd[27027]: fd cache inconsistency! 

daemon.log:
Aug 17 14:34:24 localhost mountd[27029]: spoof attempt by 192.168.XX.XXX: pretends to be localhost! 

After restarting the portmap and   sudo /etc/init.d/nfs-user-server restart  a few minutes later it resumed working...

Any ideas?

What might be related: [http://ubuntuforums.org/showthread.php?t=518681](http://ubuntuforums.org/showthread.php?t=518681)

---

