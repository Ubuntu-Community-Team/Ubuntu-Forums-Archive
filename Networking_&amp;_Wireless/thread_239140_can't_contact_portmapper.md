---
title: "can't contact portmapper"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by Román on 2006-08-18
Hello!

I'm not sure if this question belongs here.  It isn't a hardware problem, but it also isn't a Desktop problem, so here I am.

I'm having trouble setting up a nfs server between my old and my new computer.  I want to set the nfs server in the old machine.

The computer's information is:

```
rgoro@inhortomeo:~ $ uname -a
Linux inhortomeo 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686 GNU/Linux
rgoro@inhortomeo:~ $ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    720  status
    100024    1   tcp    723  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  33112  nlockmgr
    100021    3   udp  33112  nlockmgr
    100021    4   udp  33112  nlockmgr
    100021    1   tcp  32861  nlockmgr
    100021    3   tcp  32861  nlockmgr
    100021    4   tcp  32861  nlockmgr
    100005    1   udp    790  mountd
    100005    1   tcp    793  mountd
    100005    2   udp    790  mountd
    100005    2   tcp    793  mountd
    100005    3   udp    790  mountd
    100005    3   tcp    793  mountd
rgoro@inhortomeo:~ $ cat /etc/hosts.allow
rpc.mountd: 192.168.1.0/255.255.255.0
portmap: 192.168.1.0/255.255.255.0
rgoro@inhortomeo:~ $ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/rgoro exopotamia(ro,sync)
``` 

and 

```

rgoro@exopotamia:~$ uname -a
Linux exopotamia 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64 GNU/Linux
rgoro@exopotamia:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    633  status
    100024    1   tcp    636  status
rgoro@exopotamia:~$
``` 

Both machines are plugged to a DSL router.

The errors are:

```

root@exopotamia:~# mount -v -t nfs inhortomeo:/home/rgoro/ test/
mount to NFS server 'inhortomeo' failed: server is down.
RPC Error: 12 ( Remote system error )
System Error: 111 (Connection refused)
root@exopotamia:~# rpcinfo -p inhortomeo
rpcinfo: can't contact portmapper: RPC: Remote system error - Connection refused
``` 

I can connect from the new pc to the old one trough ssh and http.....

I've done all I could do by reading the man pages (rpc.*, mount, nfs, portmap) so now I'm kind off puzzled. ](*,)  Isn't this supposed to Just Work?  I'm I missing something?  I'm I not showig enough information???

Any hint, pointer, cluestick or anything will be more than welcome.

---

### Post by Román on 2006-08-22
mmm No answers... 

I'll pump the thread up and if I don't get any answers, I suppose this was the wrong place to ask....

---

