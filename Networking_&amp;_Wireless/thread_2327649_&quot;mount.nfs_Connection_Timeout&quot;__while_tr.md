---
title: "&quot;mount.nfs: Connection Timeout&quot; : while trying to mount a drive on a network machine"
date: 2016-06-13
forum: Networking &amp; Wireless
---

### Post by 1geeky on 2016-06-13
Hi,
I've connected my ubuntu 16.04 laptop to a Windows 8.1laptop via network cable and have pings from both boxes. Also, can browse through shared folders of Windows machine with nautilus. I'm going to save **ddrescue** 's output on the Windows machine's HDD. So tired to mount its drive from my ubuntu system first. the command was:
```
sudo /sbin/mount.nfs -w 192.168.253.1:/Users/Jason/Desktop /mnt/network_bkp/
``` 
But after a while I get this error: mount.nfs: ConnectionTimeout.

I've read several topics with "mount.nfs: Connection Timeout" but couldn't overcome the problem yet. As an example, added below line in the /etc/hosts.allow (Since Have read about RPC's potential role in my issue) but the problem has still remained.

```
rpcbind mountd nfsd statd lockd rquotad : 127.0.0.1, 192.168.253.1

```

Thanks

---

### Post by 1geeky on 2016-06-15
bump

---

