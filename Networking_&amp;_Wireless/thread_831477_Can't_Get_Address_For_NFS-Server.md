---
title: "Can't Get Address For NFS-Server"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by lightnb on 2008-06-16
I've followed the instructions here: [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto), and have run into an error.

On the client, when I run the mount command:

```
# mount -t nfs4 -o proto=tcp,port=2049 GlassFishIV:/ /mnt
```

I get:

```
mount.nfs4: can't get address for GlassFishIV
```

If I try:

```
# mount -t nfs4 -o proto=tcp,port=2049 192.168.5.21:/ /mnt
```

I get:

```
mount.nfs4: No such device
```


(The servers host name is "GlassFishIV" and IP is static: "192.168.5.21")


Please help?

---

### Post by PC-Ente on 2008-09-11
I Dont Know if u Need Help anymore, but here my resolution:

just mount the NFS-Share normal the first time like:

```
sudo mount {nfs_server}:/folder/folder /folder/folder
```

if that works, unmount the folder, and try it again with

```
mount -t nfs4
```

worked fine for me :)

---

