---
title: "NAS won't mount over NFS"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by tilmaniac on 2007-11-01
Hi, 

I have a NAS from which I'd like to mount an NFS share.  Whenever I try to do this, the connection times out:

> 
tilman@hostname:~$ sudo mount x.x.x.x:/Volume/Share /home/tilman/Z
[sudo] password for tilman:
mount.nfs: mount to NFS server 'x.x.x.x' failed: timed out, retrying
mount.nfs: mount to NFS server 'x.x.x.x' failed: timed out, retrying
mount.nfs: mount to NFS server 'x.x.x.x' failed: timed out, retrying
mount.nfs: mount to NFS server 'x.x.x.x' failed: timed out, retrying
mount.nfs: mount to NFS server 'x.x.x.x' failed: timed out, giving up
tilman@hostname:~$


I pretty much followed these guides:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

And here is my /etc/fstab entry
> 
# NAS
 x.x.x.x:/Volume/Share /home/tilman/Z nfs defaults 0 0


Here is rpcinfo:
client:
> 
tilman@hostname:~$ rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  34200  status
    100024    1   tcp  40585  status

server:
> 
tilman@Laura:~$ rpcinfo -p x.x.x.x
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100021    1   udp   1024  nlockmgr
    100021    3   udp   1024  nlockmgr
    100021    4   udp   1024  nlockmgr
    100005    1   udp    822  mountd
    100005    1   tcp    825  mountd
    100005    2   udp    822  mountd
    100005    2   tcp    825  mountd
    100005    3   udp    822  mountd
    100005    3   tcp    825  mountd


I'm completely out of ideas, as far as I can tell everything is working.  I don't know what to try anymore. 

FYI, I can mount the share using SMB from the Nautilus "Connect to Server" dialog.

---

