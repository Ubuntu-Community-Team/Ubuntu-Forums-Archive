---
title: "NFS not running: permission denied &amp; missing &quot;status&quot; daemon"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by liemho on 2007-06-07
Can anyone please help?
I'm new here and trying to setup NFS server but after setting up everything, the client was denied permission when trying to mount to server.

Is it possible because of my "status" daemon not running?

Here is what the printout from SERVER:
[B]# rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32768  nlockmgr
    100021    3   udp  32768  nlockmgr
    100021    4   udp  32768  nlockmgr
    100021    1   tcp  55647  nlockmgr
    100021    3   tcp  55647  nlockmgr
    100021    4   tcp  55647  nlockmgr
    100005    1   udp    882  mountd
    100005    1   tcp    885  mountd
    100005    2   udp    882  mountd
    100005    2   tcp    885  mountd
    100005    3   udp    882  mountd
    100005    3   tcp    885  mountd[/B]


on the client side, I typed in this command to try to mount it to server
[B]$ mount SERVER:/mnt /mnt/nfstest/
mount: SERVER:/mnt failed, reason given by server: Permission denied
[/B]
I already setup the **/etc/host, /etc/hosts.allow, /etc/hosts.deny **files but nothing works. so I suspect that it could be because of the status daemon on the server not running...
can anyone tell me how to install that?

Thanks for the help!

---

