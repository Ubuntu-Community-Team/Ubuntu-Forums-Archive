---
title: "mount.nfs: access denied by server while mounting"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by cwmoser on 2009-01-30
My NFS server is located at 192.168.0.203
Linux PCs on the 192.168.0.xx net can mount the NFS share.

But, for computers on the 172.16.229.xxx network, I get this error ...

mount.nfs: access denied by server while mounting

... when trying to mount from a computer off the network: 172.16.229.147


Both computers can ping each other.

In the NFS Server I have for /etc/hosts.allow:
ALL:  LOCAL
172.16.229.147

In /etc/exports I have:
/home     *(rw,sync,no_root_squash)


Does NFS work across subnets?


Carl

---

### Post by upengan78 on 2009-07-29
> **cwmoser said:**
> My NFS server is located at 192.168.0.203
Linux PCs on the 192.168.0.xx net can mount the NFS share.

But, for computers on the 172.16.229.xxx network, I get this error ...

mount.nfs: access denied by server while mounting

... when trying to mount from a computer off the network: 172.16.229.147


Both computers can ping each other.

In the NFS Server I have for /etc/hosts.allow:
ALL:  LOCAL
172.16.229.147

In /etc/exports I have:
/home     *(rw,sync,no_root_squash)


Does NFS work across subnets?


Carl


Hi Carl,


could you tell me how did u solve this issue? I am having similar error while I am trying to mount NFS share from a server on jeos(ubunutu)

---

