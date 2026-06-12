---
title: "Mounting a Nas unit share on ubuntu?"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by vwfix on 2007-05-01
I am really new to linux, and I am trying to mount a share to my ubuntu machine, form my ReadyNas unit. I have enabled NFS service on my nas.
But when I type in
 sudo mount //192.168.6.139/media

 it tells me that the directory was not found in /etc/fstab or etc/mtab

What am i doing wrong any help would be appreciated.

---

### Post by vwfix on 2007-05-01
Okay nevermind I finally got it to work was a permission problem plus not specifying the mount point

---

### Post by landowner on 2007-05-10
I'm having the same error could you specify what you did to correct it?  Thanks.

---

### Post by owen_pg on 2007-05-10
On my client, /etc/fstab shows:
192.168.20.130:/VMWare /mnt/VMWare nfs rw,users,rsize=32768,wsize=32768,soft

I don't have DNS set up so I'm just using the static address of the NFS export (on a Infrant ReadyNAS).

If you have a NFS server  that supports NFS over TCP, add that into the line in /etc/fstab because it makes the connection more robust.

Owen

P.S. (I have a problem with 7.04 actually writing to these NFS mounts from my Infrant ReadyNas NV+ - see separate posting for details.)

---

