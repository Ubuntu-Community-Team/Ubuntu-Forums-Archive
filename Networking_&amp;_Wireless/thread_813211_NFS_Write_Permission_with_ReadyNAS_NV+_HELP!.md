---
title: "NFS Write Permission with ReadyNAS NV+ HELP!"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by joecrappa on 2008-05-30
Hi all,

I'm trying to set up write permissions to my ReadyNAS via NFS. I have NFS enabled on the NAS and I'm able to browse the folders, but I can't write to it. 

I have input my ubuntu box's hostname for root access and still no luck, under root or my account. 

I'm pretty much at a loss here, as I don't know NFS very well. I know I have to enable "no_root_squash" on my client side, but I don't know where to input it. 

Any help or suggestions would be greatly appreciated. 

Here is my fstab entry for the mount:

> nas:/media      /home/jaime/done   nfs 	nfsvers=3,rsize=65536,wsize=65536,tcp,noatime,intr

Help!!!

---

