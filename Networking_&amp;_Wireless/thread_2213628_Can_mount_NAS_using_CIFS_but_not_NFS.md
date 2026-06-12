---
title: "Can mount NAS using CIFS but not NFS"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by uwe-bungto on 2014-03-27
Either of these fstab entries work for me until lately with a D-Link DNS-321 and two Linux boxes running 12.04 LTS 
```

192.168.0.14:/Volume_1        /mnt         nfs    defaults 0 0
or
[CODE]
192.168.0.14:/Volume_1        /mnt          cifs  guest,_netdev,noperm  0  0

```

Now only mounting possibility is CIFS. The code in each fstab is basically a cut n paste so they should be identical.

The D-Link is quite old and does not support NFSv4

Has there been changes to the NFS structure?

```
192.168.0.14:/Volume_1        /mnt         nfs    defaults 0 0
jpb@Maple:~$ sudo mount -av

mount.nfs: timeout set for Thu Mar 27 15:19:28 2014
mount.nfs: trying text-based options 'vers=4,addr=192.168.0.14,clientaddr=192.168.0.102'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'addr=192.168.0.14'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.0.14 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.0.14 prog 100005 vers 3 prot UDP port 32774
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.0.14:/Volume_1
```

---

### Post by apohal9 on 2014-03-29
> **uwe-bungto said:**
> 
```

mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.0.14:/Volume_1
```

Last line in your output is quite clear. The server denied your mount request.

---

### Post by uwe-bungto on 2014-04-05
> **apohal9 said:**
> Last line in your output is quite clear. The server denied your mount request.

That is obvious. The question is why would the server accept the request from one box  and deny the request another one? The request is a simple  cut and paste into each fstab.

---

### Post by uwe-bungto on 2014-04-22
An I the only one that has a problem with a NAS??

---

### Post by SeijiSensei on 2014-04-23
Are you sure the NAS is configured with "[no_root_squash]("http://linux.die.net/man/5/exports")" or what its equivalent on the D-Link may be?  Connections from fstab take place as the root user.

---

