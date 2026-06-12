---
title: "NFS Connection Hang"
date: 2020-11-17
forum: Networking &amp; Wireless
---

### Post by weswitt on 2020-11-17
I'm struggling to get a working NFS server/client. I have the server up and running as well as the client bits installed.


On the client a "showmount -e" works and responds quickly. However when I try to mount the mount command runs for a very long time and eventually times out. I get this: "mount.nfs: Connection timed out". If I run the mount command on the server then it completes as expected.


What can I do to diagnose this and make it work?

From the client:
```
$ nmap -p 111,2049 -T4 -A 192.168.1.189
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2020-11-17 23:35 UTC
Nmap scan report for WEATHERPC.WITTFAMILY.COM (192.168.1.189)
Host is up (0.00073s latency).


PORT     STATE SERVICE VERSION
111/tcp  open  rpcbind 2-4 (RPC #100000)
| rpcinfo:
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      34315/udp6  mountd
|   100005  1,2,3      46947/tcp6  mountd
|   100005  1,2,3      47331/tcp   mountd
|   100005  1,2,3      54660/udp   mountd
|   100021  1,3,4      33392/udp6  nlockmgr
|   100021  1,3,4      46225/tcp   nlockmgr
|   100021  1,3,4      46605/tcp6  nlockmgr
|   100021  1,3,4      48653/udp   nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
2049/tcp open  nfs_acl 3 (RPC #100227)
```


From the server:
```
# rpcinfo -p
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100005    1   udp  39484  mountd
    100005    1   tcp  60621  mountd
    100005    2   udp  48592  mountd
    100005    2   tcp  60225  mountd
    100005    3   udp  54660  mountd
    100005    3   tcp  47331  mountd
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    3   tcp   2049
    100003    3   udp   2049  nfs
    100227    3   udp   2049
    100021    1   udp  48653  nlockmgr
    100021    3   udp  48653  nlockmgr
    100021    4   udp  48653  nlockmgr
    100021    1   tcp  46225  nlockmgr
    100021    3   tcp  46225  nlockmgr
    100021    4   tcp  46225  nlockmgr
```

---

### Post by SeijiSensei on 2020-11-18
Use "mount -v" to see what is happening on the client.  

I do all my NFS mounts in /etc/fstab.

---

