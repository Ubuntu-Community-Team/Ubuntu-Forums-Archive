---
title: "Problem starting NFS"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by antaresjhw on 2007-03-12
I have been trying to get NFS up and running for a while on my server, and as of yet have been unable to do so.  Here is the command when I try to restart the NFS server, and the command output:

$ /etc/init.d/nfs-kernel-server restart
 * Stopping rpc mountd...
start-stop-daemon: warning: failed to kill 4052: Operation not permitted
   ...done.
 * Stopping rpc nfsd...
start-stop-daemon: warning: failed to kill 4039: Operation not permitted
start-stop-daemon: warning: failed to kill 4038: Operation not permitted
start-stop-daemon: warning: failed to kill 4037: Operation not permitted
start-stop-daemon: warning: failed to kill 4036: Operation not permitted
start-stop-daemon: warning: failed to kill 4035: Operation not permitted
start-stop-daemon: warning: failed to kill 4034: Operation not permitted
start-stop-daemon: warning: failed to kill 4033: Operation not permitted
start-stop-daemon: warning: failed to kill 4032: Operation not permitted
   ...done.
 * Unexporting directories for NFS kernel daemon...
exportfs: could not open /var/lib/nfs/etab for locking
exportfs: can't lock /var/lib/nfs/etab for writing
   ...done.
 * Exporting directories for NFS kernel daemon...
exportfs: could not open /var/lib/nfs/etab for locking
exportfs: can't lock /var/lib/nfs/etab for writing
   ...done.
 * Starting rpc nfsd...
   ...fail!


Any ideas?  I have tried to look around and see what might be causing this, but have not had any luck thus far.  If I have overlooked some previous posts or documentation that can help me out with this a point in the right direction would be appreciated.

Thanks!

---

### Post by Mr. C. on 2007-03-12
Only the superuser can perform these operations.

Use sudo.

MrC

---

