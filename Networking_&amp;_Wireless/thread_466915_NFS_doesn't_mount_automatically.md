---
title: "NFS doesn't mount automatically"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by sickrandir on 2007-06-07
In home LAN I have a server with some NFS shared folders on it (running Dapper Drake server edition). The clients are also installed with ubuntu but the latest feisty (ubuntu).
My problem is that from my pc the NFS shares doesn't mount at boot and I always have to manually mount each. Command line mount works perfectly but I can't understand why with the same configuration my brother's pc mounts all the shares at boot.

Lines from my /etc/fstab:

```

192.168.1.7:/home/admin/web /home/kinto/webserver nfs defaults 0 0
192.168.1.7:/home/admin/incoming /home/kinto/incoming nfs defaults 0 0
192.168.1.7:/home/admin/torrenti /home/kinto/torrenti nfs defaults 0 0

```

These are the same lines that are placed also in my brother's /etc/fstab.
I don't know what I am missing...

Any suggestion would be really appreciated!!
Thank you


Simone

---

### Post by turinglabs on 2007-06-07
I would take a look in the syslog or 'dmesg' output to see if there were any errors during boot when the filesystem mount-attempt took place. You might also try the standard NFS mount parameters in fstab, as opposed to 'defaults' (from nfs(5)):

```

192.168.1.7:/home/admin/web    /home/kinto/webserver   nfs  rsize=8192,wsize=8192,timeo=14,intr

```

---

