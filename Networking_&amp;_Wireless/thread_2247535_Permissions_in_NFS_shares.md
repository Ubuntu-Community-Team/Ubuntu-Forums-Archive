---
title: "Permissions in NFS shares"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by MSPdwalt on 2014-10-08
I have a subversion server (nfs client) and a php script that exports code (websites under development) from the subversion repositories.  I need them to go directly to my document root on another web server (nfs server).  So what I did was export the document root on my web server to the IP of my subversion server, then I mounted the share to a directory on my subversion server.

I added lines to my fstabs on both servers and everything mounted nicely.  When I ls -l the mount point on subversion server (nfs client) I see the directories with the appropriate permissions on my web server (nfs server).  Despite this, I cannot write files over NFS.  The UIDs and GIDs match on both systems. NFS server is Ubuntu 12.04, NFS client is Ubuntu 14.04.

here is my /etc/exports
```
/export        10.80.7.73/32(rw,fsid=0,insecure,no_subtree_check,async)
/export/demo    10.80.7.73/32(rw,nohide,insecure,no_subtree_check,async)

```

here is my fstab from the web server (NFS Server)

```
/var/storage/www/vhosts/docroot/    /export/demo   none    bind  0  0
```

here is my fstab from the subversion server (NFS Client)

```
10.80.7.70:/demo /var/storage/demo nfs    auto  0  0
```

Any advice would be greatly appreciated.

---

### Post by TheFu on 2014-10-09
If the uid and gids match between the systems and you aren't trying to use root from the remote system, I don't have a clue.  programs that run as root cannot write to NFS storage by default. There is a specific setting to override that, no_root_squash.

I've never used SVN - does it run as root?

---

### Post by MSPdwalt on 2014-10-13
Thanks! That did it.  svn hooks into apache and runs as whatever UID/GID you have apache using.

---

