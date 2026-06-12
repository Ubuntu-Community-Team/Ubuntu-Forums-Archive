---
title: "NFS problem"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by dmsn on 2007-01-05
Hey
I tested NFS on my box today and it didnt work that good.

server:~# sudo /etc/init.d/nfs-kernel-server restart
Stopping NFS kernel daemon: mountd nfsd.
Unexporting directories for NFS kernel daemon....
Exporting directories for NFS kernel daemon...exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export         "192.168.0.5:/mnt/test".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
.
Starting NFS kernel daemon: nfsd mountd.
server:~#

/etc/exportfs
/mnt/test                     192.168.0.5(rw,async)

server:~# rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    967  status
    100024    1   tcp    970  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32796  nlockmgr
    100021    3   udp  32796  nlockmgr
    100021    4   udp  32796  nlockmgr
    100021    1   tcp  55311  nlockmgr
    100021    3   tcp  55311  nlockmgr
    100021    4   tcp  55311  nlockmgr
    100005    1   udp    840  mountd
    100005    1   tcp    843  mountd
    100005    2   udp    840  mountd
    100005    2   tcp    843  mountd
    100005    3   udp    840  mountd
    100005    3   tcp    843  mountd
server:~#



What can the problem be? Thanks for help!

---

