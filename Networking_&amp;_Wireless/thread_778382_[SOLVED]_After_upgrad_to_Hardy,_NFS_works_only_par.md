---
title: "[SOLVED] After upgrad to Hardy, NFS works only partly?"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Archmage on 2008-05-02
I did ugprade my server from Gusty to Hardy and now I'm not able to connect will all my NFS-shares:

Server
```

cat /etc/exports
/data 192.168.10.1/24(rw,async,no_root_squash,no_subtree_check)
/work 192.168.10.1/24(rw,async,no_root_squash,no_subtree_check)

```


Client A
```

cat /etc/fstab 
[...]
192.168.10.1:/work /work nfs rw,rsize=8192,wsize=8192,hard,intr 0 0
192.168.10.1:/data /data nfs rw,rsize=8192,wsize=8192,hard,intr 0 0

```

But only data is mounted if I try to mount work:
```

sudo mount 192.168.10.1:/work /work
mount.nfs: internal error

```


Client B
```

cat /etc/fstab 
[...]
192.168.10.1:/work /work nfs rw,rsize=8192,wsize=8192,hard,intr 0 0

```

So no data, but work isn't also not mounted:
```

sudo mount 192.168.10.1:/work /work
mount.nfs: internal error

```

All mount points exist.

Can someone help me?

---

### Post by MaindotC on 2008-05-02
I'm not familiar with NFS but do they require authentication?

---

### Post by Archmage on 2008-05-02
> **strAlan said:**
> I'm not familiar with NFS but do they require authentication?

Nope. Everyone can mount it. That is the reason why you restrict the IP-range. Eg. 192.168.10.1/24.

---

### Post by Archmage on 2008-05-05
It was (again) a firewall-problem, because NFS likes to use differnt ports.

I did now nail it down. If you have a similar problem, please take a look at the /etc/defaults/nfs*-files. There you can make it a fixed port.

---

