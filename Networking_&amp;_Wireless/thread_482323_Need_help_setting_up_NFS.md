---
title: "Need help setting up NFS"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by hypersire on 2007-06-23
Hi all - I followed the instructions on setting up NFS found here:

[http://www.linux.org/docs/ldp/howto/NFS-HOWTO/server.html](http://www.linux.org/docs/ldp/howto/NFS-HOWTO/server.html)

I believe I followed them correctly (I am posting my config files below). When I try to mount the drive on the server, I get a permission denied error.

Following the troubleshooting tips in the above how to, I made some discoveries:

1) My /etc/exports does appear to be setup correctly, but when I look at /proc/fs/nfs/exports it is empty - nothing is being exported.

2) My /var/lib/nfs/xtab is also empty.

3) When I run exportfs -ra , I receive the following errors:

"could not open /var/lib/nfs/etab for locking"
"can't lock /var/lib/nfs/etab"

When I run rpcinfo -p servername from my client, I DO see all the correct daemons.

Here is my /etc/exports:

```
~/usb 192.168.15.103 (rw)
```

Here is my /etc/hosts.deny:

```
portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL
```

My /etc/hosts.allow:

```
portmap: 192.168.15.103
lockd: 192.168.15.103
mountd: 192.168.15.103
rquotad: 192.168.15.103
statd: 192.168.15.103
```


Any suggestions would be greatly appreciated. Thanks!

---

### Post by scrooge_74 on 2007-06-23
check this [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

