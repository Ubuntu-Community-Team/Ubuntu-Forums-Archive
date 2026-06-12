---
title: "NAS /Fstab mapping help."
date: 2019-01-03
forum: Networking &amp; Wireless
---

### Post by neuman1812 on 2019-01-03
So I have a bit of a weird issue I cant resolve. My Computer is Ubuntu 18.04

I have several security cameras each with their own username and share on the NAS drive. No problems accessing them and backing up images. On my machine I have in my fstab lines to access those shares.

```
# Entry for front door camera Storage location WD Drive
192.168.1.103:/nfs/frontdoor /media/frontdoor nfs auto,_netdev,noatime,nolock,bg,intr,tcp,actimeo=1800 0 0

# Entry for driveway camera Storage location WD Drive
192.168.1.103:/nfs/driveway /media/driveway nfs auto,_netdev,noatime,nolock,bg,intr,tcp,actimeo=1800 0 0
```


I can delete/write and access those shares without issue from my ubuntu machine. I just added a new camera, same model, similar setup on the NAS, same fstab line which mounts without issue,

```
# Entry for Nursery Personal location WD Drive
192.168.1.103:/nfs/neuman /media/nursery nfs auto,_netdev,noatime,nolock,bg,intr,tcp,actimeo=1800 0 0
```

However, If I try an delete anything from that share. I get a “Read only File System” error.  The only difference with this setup is Im using an account on the nas that is already setup (neuman) rather than create a separate "nursery" user.   


So my question is,  if my machine can access those other share and have full r/w/d access,  why doesn't it give me delete/write access for the new line?

---

### Post by TheFu on 2019-01-04
NFS uses native Unix permissions.  What are the permissions for /nfs/neuman on the NFS server?  Have the userrid and groupids been properly mapped?

NFS isn't like CIFS.  CIFS permissions are controlled at mount time (almost always).  NFS permissions are controlled just like native, local, storage via chown and chmod, assuming the NFS server isn't exporting the mount as read-only. Check the /etc/exports file on the NFS server.

---

