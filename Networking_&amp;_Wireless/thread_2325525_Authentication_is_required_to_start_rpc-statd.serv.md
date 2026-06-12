---
title: "Authentication is required to start rpc-statd.service"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by motoperpetuo on 2016-05-23
I use my laptop as my NFS server and my desktop as an NFS client. I recently upgraded the desktop to Ubuntu 16.04 (it was on Ubuntu 14.04 before). The laptop/server is on Ubuntu 14.04, and I didn't' change anything on it. For some reason, after the upgrade, I had to comment out the only active line in /etc/hosts.deny on the laptop/server to get my NFS share to mount:
> 
rpcbind mountd nfsd statd lockd rquotad : ALL

/etc/hosts.allow contains references to all the network adapters on my desktop. 

After doing that, I'm able to mount the NFS share on the laptop/server on my desktop, but strangely, I'm prompted to authenticate with this message:
> 
Authentication is required to start rpc-statd.service.

I enter the root password for the desktop (OK, to be honest I think it's the root password for the desktop, but the root password is the same on both computers) and my NFS share mounts.

I'd love to be able to fix both these problems, especially the problem with having to authenticate to get my NFS share to mount. Does anyone have any ideas?

Update:

The output for 'll /sbin/rpc.statd' on the client/desktop is:
> 
-rwxr-xr-x 1 root root 77728 Apr  6 09:18 /sbin/rpc.statd*

On the laptop/server:
> 
-rwxr-xr-x 1 root root 77728 Apr  6 09:18 /sbin/rpc.statd*

No difference that I can see, except for the date, and rights seem correct so that world should be able to access rpc.statd.

---

