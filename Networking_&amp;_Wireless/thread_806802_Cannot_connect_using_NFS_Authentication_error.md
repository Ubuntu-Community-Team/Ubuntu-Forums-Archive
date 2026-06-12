---
title: "Cannot connect using NFS: Authentication error"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by tico on 2008-05-25
Hi,

I'm trying to set up NFS, but I'm having some troubles. Here's what I've done:

1. put static IPs for server (192.168.0.2 in Ubuntu Hardy) and client (192.168.0.3 in Zenwalk);
2. configured server, adding the follwing line to my /etc/exports:
> 
/media/sda1    192.168.0.3(rw)
,
editing /etc/hosts.deny and allow
and restarted it:

/etc/hosts.deny:
> 
portmap:ALL
mountd:ALL


/etc/hosts.allow:
> 
portmap: 192.168.0.3
mountd: 192.168.0.3

3. in client I do in terminal (in client to see what's running in server)
> 
root[~]# rpcinfo -p 192.168.0.2
program vers proto port
100000 2 tcp 111 portmapper
100000 2 udp 111 portmapper
100024 1 udp 57780 status
100024 1 tcp 47225 status
100003 2 udp 2049 nfs
100003 3 udp 2049 nfs
100003 4 udp 2049 nfs
100021 1 udp 46615 nlockmgr
100021 3 udp 46615 nlockmgr
100021 4 udp 46615 nlockmgr
100003 2 tcp 2049 nfs
100003 3 tcp 2049 nfs
100003 4 tcp 2049 nfs
100021 1 tcp 49477 nlockmgr
100021 3 tcp 49477 nlockmgr
100021 4 tcp 49477 nlockmgr
100005 1 udp 36833 mountd
100005 1 tcp 43494 mountd
100005 2 udp 36833 mountd
100005 2 tcp 43494 mountd


4. in client I do in terminal (in client to see what's running in client):
> 
root[~]# rpcinfo -p 192.168.0.3
program vers proto port
100000 2 tcp 111 portmapper
100024 1 udp 43623 status
100024 1 tcp 53875 status


5. in client, nfs is apparently not running, but in startup services nfsd is checked (so is rpc)
6. when I try to mount server's share in client I get the following error in terminal:

> 
root[~]# mount 192.168.0.2:/media/sda1 /media/acer
mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Authentication error
mount.nfs: internal error


So, what' s is going on? What's causing this error?
Thanks.

---

### Post by couzin2000 on 2009-07-07
I'm having the same trouble... same exact error connecting 2 pcs with NFS. What'sup witdat?

---

### Post by couzin2000 on 2009-07-25
I just reinstalled Jaunty on my server, and I'm having the same problem all over again. I never mnanaged to fix the problem in the first place.

This is strange, I run [FONT="Courier New"]rpcinfo -p 192.168.0.102[/FONT] (this is on my server, and FOR my server) and I get this:
> sebastien@sebastien-desktop:~$ rpcinfo - 192.168.0.102
Usage: rpcinfo [ -n portnum ] -u host prognum [ versnum ]
       rpcinfo [ -n portnum ] -t host prognum [ versnum ]
       rpcinfo -p [ host ]
       rpcinfo -b prognum versnum
       rpcinfo -d prognum versnum

And when I run it from my server towards the client, I get this as well:
> sebastien@sebastien-desktop:~$ rpcinfo - 192.168.0.103
Usage: rpcinfo [ -n portnum ] -u host prognum [ versnum ]
       rpcinfo [ -n portnum ] -t host prognum [ versnum ]
       rpcinfo -p [ host ]
       rpcinfo -b prognum versnum
       rpcinfo -d prognum versnum

So I'm not sure I understand... RPC is not registered to what? How do I get it to display portnumbers and version numbers? I think this is my problem...

As for authentication, I believe you may be using IPSec... perhaps simply by altering the permissions on your system you'll manage to access.

---

