---
title: "NFS problem"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by pcomelade on 2007-01-16
Hi all,

I'm trying to share a folder between 2 computers:
Ubuntu edgy 2.6.17-10-386 : NFS server
Red Hat Linux Enterprise 4 2.6.9-42.0.3.ELsmp : NFS client

Server configuration (Ubuntu Edgy):
******************************

$ cat /etc/hosts.deny
portmap: ALL
lockd: ALL
mountd: ALL
rquotad: ALL
statd: ALL

$cat /etc/hosts.allow
## NFS
# NFS client: 161.116.70.126
portmap :       161.116.70.126 : ALLOW
lockd:          161.116.70.126 : ALLOW
rquotad:        161.116.70.126 : ALLOW
statd:          161.116.70.126 : ALLOW

$cat /etc/exports
/usr/databases/      161.116.70.126(ro)

$ cat /var/lib/nfs/etab
/usr/databases  161.116.70.126(ro,sync,wdelay,hide,nocrossmnt,secure,root_squash,no_all_squash,subtree_check,secure_locks,acl,mapping=identity,anonuid=65534,anongid=65534)

$ showmount --exports
Export list for raciborski:
/usr/databases 161.116.70.126

$ rpcinfo -p
program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32886  status
    100024    1   tcp  38916  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32904  nlockmgr
    100021    3   udp  32904  nlockmgr
    100021    4   udp  32904  nlockmgr
    100021    1   tcp  53860  nlockmgr
    100021    3   tcp  53860  nlockmgr
    100021    4   tcp  53860  nlockmgr
    100005    1   udp    755  mountd
    100005    1   tcp    758  mountd
    100005    2   udp    755  mountd
    100005    2   tcp    758  mountd
    100005    3   udp    755  mountd
    100005    3   tcp    758  mountd

$ ps aux | grep portmap
daemon   20834  0.0  0.0   1708   504 ?        Ss   18:02   0:00 /sbin/portmap

$ ps aux | grep rpc
statd    17308  0.0  0.0   1744   540 ?        Ss   10:48   0:00 /sbin/rpc.statd
root     20922  0.0  0.0      0     0 ?        S<   18:07   0:00 [rpciod/0]
root     20931  0.0  0.0   1784   280 ?        Ss   18:07   0:00 /usr/sbin/rpc.mountd
501      21090  0.0  0.0   2800   756 pts/1    R+   18:33   0:00 grep rpc

$ cat /proc/fs/nfs/exports
# Version 1.1
# Path Client(Flags) # IPs


Client configuration
*****************

$ cat /proc/filesystems | grep nfs
nodev   nfs
nodev   nfs4
nodev   nfsd

$ /sbin/lsmod | grep nfs
nfsd                  278113  17
exportfs                8001  1 nfsd
nfs                   246641  0
lockd                  78449  3 nfsd,nfs
nfs_acl                 5313  2 nfsd,nfs
sunrpc                176441  13 nfsd,nfs,lockd,nfs_acl

------------------------
When I try to mount the directory in the client:
$ mount raciborski.uv.es:/usr/databases/ /mnt/
The command never stops waiting, and I finally have to stop it (Ctrl-C)

I thought it could be a problem with the firewall, but I can't mount even if I full open the firewall:

In the server (Ubuntu):
$ iptables -F
$ iptables -P INPUT ACCEPT
(or iptables -A INPUT -i eth0 -j ACCEPT)

In the client (RHLE-4):
$ /etc/init.d/iptables stop
or
$ iptables -A INPUT -i eth0 -j ACCEPT


Does anybody knows what is happening????

Thanks in advance!

M;

---

### Post by dkuhlman on 2007-02-02
My problem has a similar finger-print. 

Actually, I have two machines: warbler and thrush.  I have tried to set up nfs on both machines.  From thrush, I can mount a directory that is on warbler.  However, from warbler I cannot access a directory on thrush?  Why?

Here is what I see on the client:

```
$ mount -t nfs thrush:/home/dkuhlman/a1/Photography/Pictures Pictures
mount to NFS server 'thrush' failed: server is down.

```

I also tried adding the "-o nfsvers=2" option to the mount command, but that did not help.

Also, on the client, when I do the following:

```
$ cat /proc/filesystems | grep nfs

```

I see nothing.  Is that a problem?  If so, how do I fix it?

I've tried both nfs-user-server and nfs-kernel-server.  Neither
works.

It seems like the nfs server is running on thrush.

```
ps -ef | grep nfs
root      7807     1  0 13:27 ?        00:00:00 /usr/sbin/rpc.nfsd
dkuhlman  7832  6700  0 13:37 pts/20   00:00:00 grep nfs

```

My network seems to be working.  From warbler, I can ping thrush and from thrush, I can ping warbler.

Is there some way I can get it to give me more information?

Dave

---

### Post by seaq on 2007-05-23
Hi I'm linking this thread to the bug report bug#67175

---

