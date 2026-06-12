---
title: "nfsv4 kerberos"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by harrim on 2007-12-26
Hi,

I have a server (ubuntu 7.10) and two clients (ubuntu 7.10). The servers exports the home directory via nfs4 and kerberos. All machines are running 64bit ubuntu.

The strange thing is on one client everything is working fine, on the other I need to do some stuff manually to mount the nfs home directory after every boot.

I have to 

> 
 /etc/init.d/nfs-common stop
 mount rpc_pipefs
 /etc/init.d/nfs-common start
mount /home


to mount the home directory, syslog shows no clue what is going wrong during startup.
For me it is obvious that the mount of rpc_pipefs went wrong somehow, I just can't figure out why.

my fstab looks as follow (snippet)
> 
rpc_pipefs /var/lib/nfs/rpc_pipefs      rpc_pipefs      defaults  0       0
nfsd    /proc/fs/nfsd   nfsd    defaults        0       0

linmaster:/home /home nfs4 rw,exec,sec=krb5p,fsid=0,hard,intr 0 0


I double checked every config file I can think of, related to my issue (fstab, etc/default/*, krb5.conf) on both machines. They are basically the same. 

Does anyone know what I could do to solve my issue ? Right now I'm lost in the woods. 
I'm not sure if this forum is the right the place to post this question if you know a more suitable one please drop me a line


Thanks in advance

Harrim

---

