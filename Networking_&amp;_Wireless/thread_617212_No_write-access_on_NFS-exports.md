---
title: "No write-access on NFS-exports"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by Knutsen on 2007-11-19
Hi,

I am trying to mount some shares, which I am exporting with NFS on my homeserver. The problem is, that I cannot write to these shares although I am exporting them rw and the import seems to mount them as rw, too. Both machines are in the same subnet 192.168.178/24.

/etc/exports (on the server 192.168.178.6 ):
```
/data 192.168.178.1/24(rw,no_root_squash,async) 10.10.200.1/24(ro,async)
```

/etc/fstab (on the client 192.168.178.69 ):
```
trondheim:/data /mnt/trondheim nfs rsize=8192,wsize=8192,timeo=14,intr
```
Output of "mount": 
```
trondheim:/data on /mnt/trondheim type nfs (rw,rsize=8192,wsize=8192,timeo=14,intr,addr=192.168.178.6)
```

The funny thing is that it worked a month ago. In the meantime I changed my flat, the server and the clients have been in a different subnet 192.168.0/24, where I haven't use NFS.... Now I changed back and it doesn't work. :confused:

---

