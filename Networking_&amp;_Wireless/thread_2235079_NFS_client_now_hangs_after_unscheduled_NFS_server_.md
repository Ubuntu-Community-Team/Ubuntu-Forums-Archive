---
title: "NFS client now hangs after unscheduled NFS server shutdown"
date: 2014-07-18
forum: Networking &amp; Wireless
---

### Post by rob78 on 2014-07-18
After having set up a working NFS client/server environment the post-doc in the lab unfortunately shut down the server computer. Once restarted the client computer could mount the exported NFS share but would hang on any attempt to access its contents. In addition "ls /" also hangs. I have restarted the client NFS server and unmounted the share on the client (as well as rebooting) but any attempt at mounting/accessing the share hangs. As I said before the shutdown all was working well. I have spent a great deal of time searching online for possible solutions none of which have yet worked. I would appreciate any help I can get with this problem and thank in advance anyone who can help me out. Client and server information given below:

Server:
10.116.18.196
Ubuntu 12.04.4 LTS / precise
uname -a --> Linux hala-P9X79-IN 3.11.0-23-generic #40~precise1-Ubuntu SMP Wed Jun 4 22:06:36 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
apt-get install nfs-kernel-server
mkdir -p /export/users
mount --bind /media/INTERNALD /export/users
To /etc/fstab added    --> /media/INTERNALD        /export/users   none    bind    0       0
In /etc/default/nfs-kernel-server set     --> NEED_SVCGSSD=no
In [Mapping] section of /etc/idmapd.conf have:
     Nobody-User = nobody
     Nobody-Group = nogroup
In /etc/exports:
     /export         10.116.18.104(rw,fsid=0,insecure,no_subtree_check,async,no_root_squash)
     /export/users   10.116.18.104(rw,nohide,insecure,no_subtree_check,async,no_root_squash)
For optional portmap lockdown in /etc/hosts.deny:
     rpcbind mountd nfsd statd lockd rquotad : ALL 
and in /etc/hosts.allow:
     rpcbind mountd nfsd statd lockd rquotad : 127.0.0.1 10.116.18.196 10.116.18.104 
service nfs-kernel-server restart

Client:
10.116.18.104
BioLinux, Ubuntu 12.04.4 LTS / precise
uname -a --> Linux david-P6T-AS 3.2.0-61-generic #93-Ubuntu SMP Fri May 2 21:31:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
apt-get install nfs-common
mkdir -p /NFS_shares
mount -t nfs -o proto=tcp,port=2049 10.116.18.196:/ /NFS_shares/
For optional portmap lockdown in /etc/hosts.deny add:
     rpcbind : ALL
and in /etc/hosts.allow add:
     rpcbind : 10.116.18.196

Thanks again, R.

---

### Post by TheFu on 2014-07-18
I use autofs with a reasonable timeout, not the fstab method though I suppose that option could be used there too. **man automount **explains.  If the connection isn't really solid, then a soft mount (see the nfs options) can be used, but there are dangers.  A few sample client-side options to research: -fstype=nfs,soft,intr,rw,async

---

