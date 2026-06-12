---
title: "NFS between RH9 (server) and Ubuntu (client)"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by Smokeless on 2006-08-25
I am attempting to export a directory from a RH9 system to a new Ubuntu system (to copy stuff to the new computer).  

The RH9 system is configured as an NFS server, with portmap, rpc.statd, rpc.mountd, mfsd, lockd, etc. running.  It also exports one directory, whose status exportfs confirms.

```
/exports  192.168.1.12(ro,sync)
```

On the Ubuntu system, I have installed portmap, nfs-common, and nfs-kernel-server (although there are no exports from the Ubuntu system), and all are started in rc5.d.  Portmap and rpc.statd are reported as running.  I have a mount point (as indicated below).

Whether mounting using the fstab entry below and the command "mount /net/exports" or using the command line with the same parameters (the servername has been changed here to protect the guilty) ...

```
servername:/exports  /net/exports  nfs  ro,user,noauto,soft,intr        0    0

```

I get the same result:

RPC Error: 15 ( Program not registered )

I am new to Ubuntu, but most definitely not new to Unix, Linux, or NFS!

What might be happening?  ](*,) 
Thanks.

---

### Post by Smokeless on 2006-08-26
Smokeless?  Ne, CLUEless!

I'll answer my own query.  I thought I had already setup an appropriate hosts.allow.  Yes, I had, for my DHCP addresses at work, but not at home.  All I needed to do was to amend my /etc/hosts.allow file with the new IP addresses and masks.

Now working! :D

---

